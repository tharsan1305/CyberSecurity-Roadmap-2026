# 96 - LangGraph
## Overview
LangGraph extends LangChain with a graph-based execution model enabling stateful, cyclic, multi-agent workflows.

## Graph vs Chain
| Feature | LangChain Chain | LangGraph |
|---------|----------------|-----------|
| Execution | Linear / DAG | Cycles supported |
| State | Manual passing | Built-in schema |
| Multi-agent | Manual wiring | Native orchestration |
| Human-in-loop | Manual | Native checkpointing |

## Core Concepts
```python
from langgraph.graph import StateGraph, END
from typing import TypedDict, List

class SOCState(TypedDict):
    alert: str
    severity: str
    iocs: List[str]
    ticket_created: bool

graph = StateGraph(SOCState)
graph.add_node("triage",     triage_fn)
graph.add_node("investigate", investigate_fn)
graph.add_node("escalate",   escalate_fn)
graph.add_node("close",      close_fn)

graph.set_entry_point("triage")
graph.add_conditional_edges("triage", route_by_severity, {
    "critical": "escalate",
    "medium":   "investigate",
    "low":      "close",
})
graph.add_edge("investigate", "close")
graph.add_edge("escalate", END)
graph.add_edge("close", END)

app = graph.compile()
result = app.invoke({"alert":"Ransomware on FILE-SERVER-01","severity":"","iocs":[],"ticket_created":False})
```

## Checkpointing (Human-in-the-Loop)
```python
from langgraph.checkpoint.memory import MemorySaver
app = graph.compile(checkpointer=MemorySaver(), interrupt_before=["escalate"])
config = {"configurable": {"thread_id": "inc-001"}}

# Run until pause point
result = app.invoke({"alert": "Critical breach detected"}, config)
print("Paused for human approval:", result)

# Human reviews, then resumes
app.invoke(None, config)  # resume
```

## Use Cases
- Cyclic SOC: alert -> investigate -> gather more info -> re-assess -> decide
- Multi-agent IR: triage agent -> forensics agent -> reporting agent
- Human-in-loop: automated steps + human approval at critical points
