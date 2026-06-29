# 96 - LangGraph - Labs

## Lab 1: SOC Triage Graph
```python
from langgraph.graph import StateGraph, END
from langchain_anthropic import ChatAnthropic
from typing import TypedDict

llm = ChatAnthropic(model="claude-sonnet-4-6")

class State(TypedDict):
    alert: str
    severity: str
    recommendation: str

def triage(s):
    r = llm.invoke(f"Rate severity (Critical/High/Medium/Low) of: {s['alert']}. Reply one word only.")
    return {**s, "severity": r.content.strip()}

def recommend(s):
    r = llm.invoke(f"Alert: {s['alert']}, Severity: {s['severity']}. Give 1-sentence action.")
    return {**s, "recommendation": r.content}

def route(s):
    return "recommend" if any(x in s["severity"] for x in ["Critical","High"]) else "close"

g = StateGraph(State)
g.add_node("triage", triage)
g.add_node("recommend", recommend)
g.add_node("close", lambda s: s)
g.set_entry_point("triage")
g.add_conditional_edges("triage", route, {"recommend":"recommend","close":"close"})
g.add_edge("recommend", END)
g.add_edge("close", END)
app = g.compile()

r = app.invoke({"alert":"Mass file encryption on FILE-SERVER-01","severity":"","recommendation":""})
print(f"Severity: {r['severity']}")
print(f"Action: {r['recommendation']}")
```

## Lab 2: Multi-Agent Security System
Design 3 agents in LangGraph:
1. **Triage Agent** - classifies alert type and severity
2. **Investigation Agent** - enriches IOCs via APIs
3. **Reporting Agent** - generates incident summary

Wire with state passing between agents.

## Lab 3: Human-in-the-Loop IR
Build workflow with checkpointing that pauses before:
- Isolating a production server (requires manager approval)
- Sending external breach notification (requires legal approval)

## Practice Challenges
- [ ] Build full PICERL IR workflow in LangGraph
- [ ] Add conditional edges routing based on LLM analysis output
- [ ] Implement supervisor agent delegating to specialist sub-agents
- [ ] Complete DeepLearning.AI "AI Agents in LangGraph" course (free)
