# 🤖 Multi-Agent Customer Support & Email Automation System

A complete enterprise-grade AI system built using Google AI Studio.  
It automates customer support end-to-end using five coordinated AI agents.

This project is part of the Google AI Agents competition and showcases:
- Multi-agent orchestration  
- JSON-based structured workflow  
- Automatic email drafting  
- CRM-ready summaries  
- Escalation decision-making  
- Supervisor agent coordination




## 🧠 System Architecture (Enterprise Multi-Agent Design)

This system uses a modular enterprise-style multi-agent pipeline inspired by real customer support workflows.  
A Supervisor Agent orchestrates four specialized sub-age



```
               ┌──────────────────────────────┐
               │      Customer Email / Input   │
               └───────────────┬──────────────┘
                               ▼
                 ┌──────────────────────────────────┐
                 │   SUPERVISOR / ORCHESTRATOR      │
                 │   - Controls full workflow        │
                 │   - Coordinates all agents        │
                 │   - Combines final outputs        │
                 └───────────────┬───────────────┬──┘
                                 │               │
                ┌────────────────┘               └────────────────┐
                ▼                                                 ▼

   ┌────────────────────────────┐                     ┌──────────────────────────────┐
   │ AGENT 1: Intake &           │                     │ AGENT 4: Escalation Decision │
   │ Classification              │                     │ Engine                        │
   │ - Extracts issue type       │                     │ - Priority rules              │
   │ - Sentiment / urgency       │                     │ - Human escalation logic      │
   │ - Customer summary          │                     │ - Assigns team                │
   └───────────────┬────────────┘                     └────────────┬─────────────────┘
                   │ JSON                                            │ JSON
                   ▼                                                 ▼

        ┌──────────────────────────────┐             ┌──────────────────────────────┐
        │ AGENT 2: Reply Drafting      │             │ AGENT 3: CRM & Summary Agent │
        │ - Generates response email   │             │ - Creates CRM summary         │
        │ - Adapts tone to sentiment   │             │ - Tags + action items         │
        │ - Provides next steps        │             │ - Internal ticket output      │
        └───────────────┬──────────────┘             └──────────────┬──────────────┘
                        │ JSON                                      │ JSON
                        └──────────────────────────┬────────────────┘
                                                   ▼
                                 ┌───────────────────────────────────┐
                                 │      Final Output Layer            │
                                 │ - Combined workflow output          │
                                 │ - Final decision (auto/escalate)   │
                                 │ - Final status                      │
                                 └────────────────────────────────────┘
```
