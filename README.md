# 🤖 DAY 08 — AI Invoice Analyzer

An AI-powered Invoice Analyzer built with **n8n** that automatically analyzes invoice data, extracts important information, validates invoice details, identifies missing information, categorizes expenses, and generates an overall quality score.

This project is part of my **30 Days AI Automation Challenge**, where I am building practical AI-powered automation projects using n8n and AI.

---

## 🚀 Project Overview

Invoice processing is an important but repetitive business task. Manually checking invoices for missing information, incorrect values, tax details, payment status, and other financial data can take significant time.

The **AI Invoice Analyzer** automates the initial invoice analysis process.

The workflow receives invoice information and uses AI to analyze the available data, identify important fields, detect missing information, categorize the expense, validate the invoice, and generate a quality score.

This helps businesses quickly identify invoices that are complete and invoices that require manual review.

---

## 🎯 Main Objective

The main objective of this project is to build an AI-powered invoice intelligence system that can:

- 📄 Analyze invoice information
- 🔍 Extract important invoice fields
- 💰 Identify financial information
- 🧾 Analyze invoice details
- 🏷️ Categorize expenses
- ✅ Validate invoice information
- ⚠️ Detect missing information
- 📊 Generate an invoice quality score
- 🚨 Identify invoices requiring manual review
- 🤖 Generate structured JSON output
- ⚡ Reduce manual invoice-processing work

---

## ✨ Key Features

### 📄 Invoice Data Extraction

The AI analyzes available invoice information and identifies important fields such as:

- Invoice Number
- Invoice Date
- Due Date
- Vendor Name
- Customer Name
- Account Number
- Previous Charges
- Current Charges
- Subtotal
- Tax
- Total Amount
- Currency
- Payment Status
- Line Items
- Quantity
- Unit Price

### 🔍 Invoice Validation

The workflow checks whether important invoice information is available and usable.

It can detect:

- Missing invoice number
- Missing invoice date
- Missing due date
- Missing vendor information
- Missing customer information
- Missing subtotal
- Missing tax amount
- Missing total amount
- Missing payment status
- Missing line-item information
- Missing quantities
- Missing unit prices
- Invalid numeric values
- Ambiguous currency
- Suspicious account information

### 🏷️ Expense Categorization

The AI automatically categorizes the invoice based on the available information.

Possible categories include:

- Utilities
- Office Supplies
- Software
- Travel
- Marketing
- Equipment
- Professional Services
- Rent
- Transportation
- Food
- Inventory
- Other

### 📊 Quality Score

Each invoice receives a quality score between **0 and 100**.

The score represents how complete and reliable the available invoice information is.

- 90–100 → Excellent
- 70–89 → Good
- 50–69 → Moderate
- 25–49 → Poor
- 0–24 → Very Poor

### 🚨 Validation Status

The AI generates a validation status based on the invoice information.

Possible statuses include:

- Valid
- Needs Review
- Incomplete
- Invalid

### ⚠️ Missing Information Detection

The system identifies exactly what is missing from an invoice.

Examples:

- Invoice number
- Subtotal
- Tax amount
- Payment status
- Line-item quantities
- Line-item unit prices
- Clear currency code
- Account information

### 👀 Manual Review Detection

The system determines whether an invoice should be reviewed manually.

If important information is missing or suspicious, the workflow flags the invoice for manual review.

---

## 🔄 Workflow Architecture

Invoice Input  
↓  
Data Processing  
↓  
AI Invoice Analysis  
↓  
Structured Output  
↓  
Invoice Validation  
↓  
Quality Score  
↓  
Expense Categorization  
↓  
Missing Information Detection  
↓  
Manual Review Decision  
↓  
Final Invoice Analysis

---

## 🛠️ Technologies Used

- **n8n** — Workflow automation platform
- **AI / LLM** — Invoice analysis and intelligence
- **JSON** — Structured data exchange
- **Webhooks / Workflow Inputs** — Data ingestion
- **JavaScript / n8n Expressions** — Data processing
- **Prompt Engineering** — AI instruction design

---

## 🧩 Workflow Process

### 1. Invoice Input

The workflow receives invoice information as input.

The input can contain information such as vendor, invoice date, total amount, currency, expense category, charges, tax, and other available invoice details.

### 2. Data Processing

The incoming information is prepared for AI analysis.

The workflow organizes the invoice data so that the AI model can understand and analyze it effectively.

### 3. AI Invoice Analysis

The AI analyzes the provided invoice information.

It attempts to identify:

- Vendor
- Customer
- Invoice number
- Dates
- Previous charges
- Current charges
- Subtotal
- Tax
- Total amount
- Currency
- Line items
- Payment status
- Account information
- Expense category

The AI is instructed not to invent missing information.

### 4. Structured Output

The AI response is returned in a structured JSON format.

This makes the result easy to process using additional n8n nodes.

### 5. Validation

The workflow evaluates the extracted invoice information and checks whether important fields are available and usable.

### 6. Missing Information Detection

The system generates a list of missing or incomplete fields.

### 7. Quality Score

The invoice receives a quality score between 0 and 100 based on the completeness and reliability of the available information.

### 8. Expense Categorization

The AI determines the most appropriate expense category based on the invoice information.

### 9. Final Output

The final output contains:

- Invoice details
- Financial information
- Expense category
- Validation status
- Quality score
- Missing information
- Review requirement
- Summary

---

## 🧠 AI Prompt

The core AI prompt used in the workflow:

You are an expert AI Invoice Analyzer.

Analyze the provided invoice information carefully.

Your task is to:

1. Extract all available invoice information.
2. Identify the invoice number.
3. Identify invoice date and due date.
4. Identify vendor and customer information.
5. Extract previous charges if available.
6. Extract current charges if available.
7. Extract subtotal.
8. Extract tax amount.
9. Extract total amount.
10. Identify the currency.
11. Extract available line-item information.
12. Identify payment status.
13. Identify account information if available.
14. Categorize the expense.
15. Detect missing or incomplete information.
16. Validate the invoice.
17. Generate a quality score from 0 to 100.
18. Determine whether the invoice requires manual review.
19. Provide a concise summary of the invoice condition.

IMPORTANT RULES:

- Do not invent information.
- Do not guess missing values.
- If information is unavailable, return null.
- If a field is incomplete, identify it in missing_information.
- Numeric financial fields must contain numeric values only.
- Clearly distinguish between currency symbols and currency codes.
- Identify suspicious or placeholder information.
- Review the complete invoice context before generating the score.
- Return ONLY valid JSON.

Use the following structure:

{
  "invoice_number": null,
  "invoice_date": null,
  "due_date": null,
  "vendor_name": null,
  "customer_name": null,
  "previous_charges": null,
  "current_charges": null,
  "subtotal": null,
  "tax": null,
  "total_amount": null,
  "currency": null,
  "expense_category": null,
  "payment_status": null,
  "line_items": [],
  "account_number": null,
  "validation_status": null,
  "quality_score": 0,
  "missing_information": [],
  "review_required": false,
  "summary": null
}

---

## 📦 Example Input

{
  "Vendor": "ABC Utilities",
  "Invoice Date": "2026-08-10",
  "Total Amount": 9882,
  "Currency": "$",
  "Expense Category": "Utilities"
}

---

## 📤 Example AI Output

{
  "invoice_number": null,
  "invoice_date": "2026-08-10",
  "due_date": null,
  "vendor_name": "ABC Utilities",
  "customer_name": null,
  "previous_charges": null,
  "current_charges": null,
  "subtotal": null,
  "tax": null,
  "total_amount": 9882,
  "currency": "$",
  "expense_category": "Utilities",
  "payment_status": null,
  "line_items": [],
  "account_number": null,
  "validation_status": "Needs Review",
  "quality_score": 25,
  "missing_information": [
    "Invoice number",
    "Numeric amount for previous charges",
    "Numeric amount for current charges",
    "Numeric amount for tax",
    "Subtotal",
    "Tax amount",
    "Line-item quantities",
    "Line-item unit prices",
    "Payment status",
    "Clear currency code",
    "Account number appears to be placeholder text"
  ],
  "review_required": true,
  "summary": "The invoice contains a total amount and expense category but lacks several important fields required for complete validation."
}

---

## 📊 Sample Analysis

| Field | Result |
|---|---|
| Total Amount | 9882 |
| Currency | $ |
| Expense Category | Utilities |
| Validation Status | Needs Review |
| Quality Score | 25/100 |
| Review Required | Yes |

---

## ⚙️ Setup Instructions

### Step 1 — Create n8n Workflow

Create a new workflow in n8n and configure the workflow input or webhook.

### Step 2 — Add Invoice Data

Provide invoice information to the workflow.

### Step 3 — Configure AI Node

Add your preferred AI model and provide the AI Invoice Analyzer prompt.

Make sure the AI is instructed to return JSON only.

### Step 4 — Configure Structured Output

Ensure the AI response follows the defined JSON structure.

### Step 5 — Add Validation Logic

Process:

- Validation Status
- Quality Score
- Missing Information
- Review Requirement
- Expense Category

### Step 6 — Test Workflow

Send different invoice examples through the workflow and verify the generated results.

---

## 🧪 Testing Scenarios

### Test 1 — Complete Invoice

Expected:

- Validation Status → Valid
- Review Required → False
- High Quality Score

### Test 2 — Partially Complete Invoice

Expected:

- Validation Status → Needs Review
- Review Required → True
- Medium Quality Score

### Test 3 — Highly Incomplete Invoice

Expected:

- Validation Status → Incomplete
- Review Required → True
- Low Quality Score

### Test 4 — Invalid Information

Expected:

- Validation Status → Invalid
- Review Required → True

---

## 🎯 Business Use Cases

The AI Invoice Analyzer can be useful for:

- 🏢 Small Businesses
- 💼 Accounting Departments
- 🧾 Finance Teams
- 🛒 Procurement Departments
- 📊 Expense Management
- 🏦 Financial Operations
- 📦 Vendor Management
- 🤝 Accounts Payable
- 🧑‍💼 Administrative Teams
- 📑 Invoice Processing Systems

---

## 💡 Real-World Problem Solved

Traditional invoice processing often requires employees to manually inspect documents and enter information into systems.

This creates several problems:

- ⏳ Time-consuming manual work
- ❌ Human errors
- 🔍 Difficult validation
- 📄 Missing information
- 💰 Incorrect financial values
- ⚠️ Delayed invoice processing

The AI Invoice Analyzer addresses these problems by automating the first stage of invoice intelligence.

Instead of manually checking every invoice, users can focus on invoices that have been flagged for review.

---

## 🔐 Data Validation Philosophy

Financial information should never be guessed.

Therefore, this project follows an important rule:

> **If the information is not available, the AI should not invent it.**

Missing values are returned as `null` and identified through the `missing_information` field.

This makes the system safer and more reliable for financial automation.

---

## 📈 Future Improvements

Possible improvements include:

- 📄 PDF invoice extraction
- 🖼️ OCR for scanned invoices
- 📧 Automatic email invoice processing
- ☁️ Google Drive integration
- 📊 Google Sheets invoice database
- 🗄️ Database storage
- 📬 Automatic approval emails
- 🔔 Slack/Teams notifications
- 🧾 Automatic invoice report generation
- 🔍 Duplicate invoice detection
- 💰 Tax calculation verification
- 📅 Due-date monitoring
- 🚨 Suspicious invoice detection
- 📊 Financial dashboards
- 🔐 Advanced validation rules
- 🤖 Automatic invoice approval workflow

---

## 🏆 Project Outcome

The completed project demonstrates how AI and workflow automation can be combined to build a practical business automation system.

The workflow transforms raw invoice information into structured and actionable intelligence.

Receive Invoice  
↓  
Process Data  
↓  
Analyze With AI  
↓  
Extract Information  
↓  
Validate Invoice  
↓  
Detect Missing Information  
↓  
Categorize Expense  
↓  
Generate Quality Score  
↓  
Determine Review Status  
↓  
Generate Final Report

---

## 📁 Project Structure

DAY-08-AI-INVOICE-ANALYZER/

├── README.md  
├── workflow/  
│   └── invoice-analyzer-workflow.json  
├── samples/  
│   └── sample-invoice.json  
├── screenshots/  
│   └── workflow.png  
└── LICENSE

---


## 🔗 GitHub Repository

https://github.com/JunaidZulfiqar07/DAY-08-AI-INVOICE-ANALYZER

---

## 🧑‍💻 Author

### Junaid Zulfiqar

Computer Engineering Student  
UET Taxila


### Stay tuned for Day 09! 🔥
