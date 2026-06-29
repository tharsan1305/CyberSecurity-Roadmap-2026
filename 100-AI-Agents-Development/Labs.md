# 100 - AI Agents Development - Labs

## Lab 1: Security Triage Agent
```python
import anthropic, json
client = anthropic.Anthropic(api_key='YOUR_KEY')

tools = [
    {'name':'check_ip','description':'Check IP reputation','input_schema':{'type':'object','properties':{'ip':{'type':'string'}},'required':['ip']}},
    {'name':'check_url','description':'Check URL on VirusTotal','input_schema':{'type':'object','properties':{'url':{'type':'string'}},'required':['url']}}
]

def run_tool(name, inp):
    if name=='check_ip': return f"IP {inp['ip']}: AbuseIPDB score 92/100, C2 distribution"
    if name=='check_url': return f"URL {inp['url']}: 45/90 engines flag as phishing"

def run_agent(alert):
    messages=[{'role':'user','content':f'Analyze: {alert}'}]
    while True:
        r = client.messages.create(model='claude-sonnet-4-6',max_tokens=1024,tools=tools,messages=messages)
        if r.stop_reason=='end_turn': return r.content[0].text
        for b in r.content:
            if b.type=='tool_use':
                result = run_tool(b.name, b.input)
                print(f'  -> {b.name}({b.input}) => {result}')
                messages += [
                    {'role':'assistant','content':r.content},
                    {'role':'user','content':[{'type':'tool_result','tool_use_id':b.id,'content':result}]}
                ]

print(run_agent('User clicked link http://phish.ru and entered credentials. Source IP: 185.220.101.5'))
```

## Lab 2: Add Long-Term Memory
```python
import chromadb, hashlib
from datetime import datetime

client_db = chromadb.PersistentClient('./agent_memory')
incidents = client_db.get_or_create_collection('incidents')

def store_incident(alert, analysis):
    incidents.add(documents=[f'Alert: {alert} | Analysis: {analysis}'],
                  ids=[hashlib.md5(alert.encode()).hexdigest()])

def recall_similar(alert, n=2):
    r = incidents.query(query_texts=[alert], n_results=n)
    return r['documents'][0] if incidents.count()>0 else []

# Use in agent: recall_similar(alert) -> include in system prompt as context
```

## Lab 3: CrewAI Multi-Agent Security
```python
# pip install crewai
from crewai import Agent, Task, Crew, Process
from crewai.tools import tool

@tool('IP Check')
def check_ip_tool(ip: str) -> str:
    return f'IP {ip}: reputation score 85/100, Tor exit node'

analyst = Agent(role='SOC Analyst',goal='Analyze threats',tools=[check_ip_tool],verbose=True)
writer  = Agent(role='Reporter',goal='Write incident reports',verbose=True)

triage = Task(description='Analyze alert: {alert}. Identify threat type, severity, IOCs.', agent=analyst)
report = Task(description='Write professional incident report from analysis.', agent=writer)

crew = Crew(agents=[analyst,writer],tasks=[triage,report],process=Process.sequential)
result = crew.kickoff(inputs={'alert':'Outbound C2 to 185.220.101.5 every 60 seconds'})
print(result)
```

## Practice Challenges
- [ ] Build 5-tool security agent with full audit logging
- [ ] Add memory so agent recalls previous incidents
- [ ] Create 3-agent CrewAI: Analyst + Responder + Reporter
- [ ] Add human-approval checkpoint before any destructive action
- [ ] Compare AutoGen vs CrewAI for multi-agent security workflows
