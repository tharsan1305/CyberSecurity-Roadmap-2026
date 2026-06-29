# 100 - AI Agents Development
## What is an AI Agent?
LLM-powered system that autonomously reasons, plans, and takes actions using tools.

```
Traditional LLM: Input -> LLM -> Output (one shot)
AI Agent:        Input -> Think -> Tool Call -> Observe -> Think -> Tool Call -> Final Answer
```

## ReAct Framework (Reason + Act)
```
Thought: I need to check if this IP is malicious.
Action: check_ip({ip: 185.220.101.5})
Observation: Score 98/100, Tor exit node.
Thought: High risk. I should also check open ports.
Action: shodan_lookup({ip: 185.220.101.5})
Observation: Ports 22, 80, 443 open. Tor relay.
Final Answer: 185.220.101.5 is a high-risk Tor exit node (AbuseIPDB: 98/100)
```

## Tool Calling with Anthropic API
```python
import anthropic, json
client = anthropic.Anthropic()

tools = [{
    'name': 'get_ip_info',
    'description': 'Get threat intelligence for an IP address',
    'input_schema': {'type':'object','properties':{'ip':{'type':'string'}},'required':['ip']}
}]

def get_ip_info(ip):
    return json.dumps({'ip':ip, 'abuse_score':85, 'country':'RU', 'isp':'Suspicious ISP'})

messages = [{'role':'user','content':'Is 185.220.101.5 malicious?'}]
while True:
    r = client.messages.create(model='claude-sonnet-4-6', max_tokens=1024, tools=tools, messages=messages)
    if r.stop_reason == 'end_turn':
        print(r.content[0].text); break
    if r.stop_reason == 'tool_use':
        tu = next(b for b in r.content if b.type=='tool_use')
        result = get_ip_info(**tu.input)
        messages += [
            {'role':'assistant','content':r.content},
            {'role':'user','content':[{'type':'tool_result','tool_use_id':tu.id,'content':result}]}
        ]
```

## Memory Types
| Type | Implementation |
|------|---------------|
| Short-term | Messages array in API call |
| Long-term | Vector DB (ChromaDB) or SQL DB |
| Episodic | Summarize + store past sessions |
| Semantic | Key-value store of facts |

## Multi-Agent with CrewAI
```python
from crewai import Agent, Task, Crew, Process

analyst  = Agent(role='SOC Analyst',  goal='Triage security alerts', tools=[check_ip])
responder= Agent(role='IR Responder', goal='Contain threats',         tools=[isolate_host])

triage = Task(description='Analyze alert: {alert}', agent=analyst)
remediate = Task(description='Based on analysis, contain the threat', agent=responder)

crew = Crew(agents=[analyst,responder], tasks=[triage,remediate], process=Process.sequential)
result = crew.kickoff(inputs={'alert':'Ransomware on WORKSTATION-01'})
```
