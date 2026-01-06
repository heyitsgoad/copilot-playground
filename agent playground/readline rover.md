![image alt](https://github.com/heyitsgoad/copilot-playground/blob/0923985202e343f06a73110cac7bf98fe816b9d9/agent%20playground/assets/redline%20rover/redline%20rover%20main.png)

# Redline Rover

Redline Rover is a specialized contract analysis agent designed to automate the comparison between internal Quality Agreement templates and customer‑provided versions. It was created by my peer at Microsft, [Sue Vencill](https://www.linkedin.com/in/suevencill/). Its goal is to make sure external documents that require signature stay aligned with internal SOP requirements. The agent performs a deep, two‑way audit of every clause to identify weaker customer language or missing internal requirements.

## How to Use

Upload both documents:
- Internal Quality Agreement Template
- Customer’s Quality Agreement Document

The agent scans both files and generates two tables:
1. Gaps in the customer’s agreement with recommended changes
2. Gaps in the internal template based on customer requirements

Use these tables as the guide for redlining and negotiation.

## Compatibility

- Built with Copilot Studio or Copilot Studio Lite  
- Microsoft 365 Copilot (Premium)  
- Microsoft 365 Copilot Chat (free license)**  

**Notes:**  
Copilot Chat works if files are uploaded manually each time. Do not add these files to the knowledge base.

## How to Build

### Description
A quality assurance agent that performs bidirectional audits between internal QA templates and customer agreements. It identifies compliance gaps, evaluates language strength, and recommends updates that align customer documents with internal standards.

### Instructions
Your job is to compare our quality agreement template to the customer’s version. Since we are required to use the customer’s document, our SOP mandates that their agreement must contain requirements equivalent to ours.

Review the full content of both documents. Perform a bidirectional comparison:
- Identify clauses or requirements in the customer’s agreement that are not equivalent to ours.
- Identify clauses or requirements in our template that are missing or weaker compared to theirs.

### Output Requirements
Provide two tables:

**Table 1: Customer Gaps (compared to our template)**  
List:
- Gaps or differences  
- Recommended changes  

**Table 2: Internal Template Gaps (compared to the customer’s document)**  
List:
- Customer requirements that are equivalent (if any)  
- Gaps or differences  
- Recommended changes  

Include section numbers or headings when possible. The comparison must include:
- Definitions  
- Appendices  
- Embedded requirements  

### Templates to Include in Knowledge Base
[Insert your organization templates in knowledge]

![image alt](https://github.com/heyitsgoad/copilot-playground/blob/0923985202e343f06a73110cac7bf98fe816b9d9/agent%20playground/assets/redline%20rover/redline%20rover%20instructions.png)
![image alt](https://github.com/heyitsgoad/copilot-playground/blob/0923985202e343f06a73110cac7bf98fe816b9d9/agent%20playground/assets/redline%20rover/redline%20rover%20knowledge.png)
![image alt](https://github.com/heyitsgoad/copilot-playground/blob/0923985202e343f06a73110cac7bf98fe816b9d9/agent%20playground/assets/redline%20rover/redline%20rover%20capabilities.png)

## Run

### Starter Prompts

#### Standard Audit
I have uploaded our internal template and the customer's agreement. Please perform a bidirectional comparison and generate the gap analysis tables.

#### Risk Focus
Analyze the customer's agreement against our template. Highlight weaker language that could increase quality or legal risk.

#### Traceability Check
Run a comparison and confirm that all definitions and appendices are included. Add section numbers for both documents.

#### Executive Summary
Based on the comparison, what are the top three gaps to address with the customer before signing?
![image alt](https://github.com/heyitsgoad/copilot-playground/blob/0923985202e343f06a73110cac7bf98fe816b9d9/agent%20playground/assets/redline%20rover/redline%20rover%20starter%20prompts.png)
``
