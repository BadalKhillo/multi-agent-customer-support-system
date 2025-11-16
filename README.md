
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




1. Intake & Classification Agent
	•	Reads the raw customer message
	•	Extracts key details
	•	Classifies issue type, sentiment, urgency, keywords
	•	Outputs a clean JSON summary

2. Reply Drafting Agent
	•	Takes the JSON summary
	•	Writes a high-quality, ready-to-send email reply
	•	Maintains professional tone and policy-aligned responses

3. CRM Summary Agent
	•	Converts the email + JSON into CRM-friendly notes
	•	Adds tags, priority, and next-action items
	•	Prepares Salesforce-style short summaries

4. Escalation Agent
	•	Analyzes sentiment + risk
	•	Decides if the case needs human involvement
	•	Marks cases as “auto-resolved” or “requires escalation”

5. Supervisor Agent
	•	Orchestrates all other agents
	•	Validates outputs
	•	Ensures quality, consistency, and final decision-making
	•	Returns the complete pipeline output as a single JSON object


{
  "intake_output": {
    "customer_id": "cust_789123",
    "category": "Order Issue",
    "sub_category": "Damaged Product",
    "sentiment": "Negative",
    "urgency": "High",
    "summary": "Customer reports their order arrived broken and is requesting a refund."
  },
  "draft_reply_output": {
    "subject": "Regarding Your Recent Order - We're Here to Help",
    "body": "Dear Customer,\n\nThank you for reaching out to us. We are so sorry to hear that your order arrived in a damaged condition. That is certainly not the experience we want for our customers, and we understand your frustration.\n\nWe want to make this right for you immediately. Please be assured that we are processing a full refund for your order. You should see the amount reflected in your original payment method within 3-5 business days.\n\nThere is no need to return the damaged item.\n\nWe sincerely apologize for this inconvenience and appreciate your patience. If there is anything else we can assist you with, please do not hesitate to ask.\n\nSincerely,\nThe Support Team"
  },
  "crm_output": {
    "ticket_id": "tkt_556_8901",
    "status": "Open",
    "summary_for_crm": "Customer reported a broken item and requested a refund. High urgency and negative sentiment. Drafted a reply confirming the refund.",
    "tags": ["damaged_item", "refund_request", "negative_feedback"]
  },
  "escalation_output": {
    "should_escalate": true,
    "reason": "Strong negative sentiment and direct refund request for a failed product. Human review recommended."
  },
  "final_decision": "Escalate to human agent",
  "final_status": "Pending human review"
}



🧰 Technologies Used

AI Models
	•	Gemini 2.5 Pro (reasoning + structured JSON tasks)
	•	Gemini Flash (fast reasoning + orchestration)

Agent Framework
	•	Google ADK (Agent Development Kit)
	•	Multi-agent orchestration (sequential + parallel)
	•	Supervisor–subagent pipeline

Tools
	•	Google AI Studio (prompting, agent design, testing)
	•	JSON Structured Outputs
	•	System Instructions & Context Management


	## ⚙️ Setup & How to Run

This project does not use traditional code.  
All agents are built and tested directly inside *Google AI Studio*.

### 1️⃣ Open Google AI Studio  
https://aistudio.google.com/

### 2️⃣ Create 5 prompt tabs  
One for each agent:
- Intake & Classification Agent  
- Reply Drafting Agent  
- CRM Summary Agent  
- Escalation Agent  
- Supervisor / Orchestrator Agent  

### 3️⃣ Paste the system instructions  
For each tab, paste the correct system prompt (the ones you already used in Playground).

### 4️⃣ Test the pipeline  
Use the *Supervisor Agent*:
- Paste a customer message (example: “My order arrived broken, I want a refund”)  
- The Supervisor coordinates all other agents  
- You get the final combined JSON with:
  - intake_output  
  - draft_reply_output  
  - crm_output  
  - escalation_output  
  - final_decision  
  - final_status
