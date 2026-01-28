# Invoice Processing - AP Automation

## Enterprise-Grade Invoice Workflow with Fraud Detection & Intelligent Approval Routing

Transform your accounts payable operations with this comprehensive n8n workflow that automates the entire invoice lifecycle - from receipt to approval. Built for organizations that need enterprise-grade invoice management with advanced fraud detection, vendor validation, budget tracking, and smart approval routing.

---

## Key Features

- **Multi-method Duplicate Detection** - Prevents double payments with primary, secondary, and fuzzy fingerprint matching
- **Vendor Risk Scoring** - Validates vendors against approved database with spending limits and risk assessment
- **Automatic Line Item Categorization** - AI-powered categorization with budget tracking and alerts
- **Fraud Detection Engine** - Flags suspicious patterns including round numbers, rushed payments, and suspicious items
- **Early Payment Optimization** - Calculates discount opportunities and annualized ROI
- **Smart Approval Routing** - Auto-approves low-risk invoices, routes others to managers or directors

---

## How It Works

```
Email Received → Extract Invoice Data → Duplicate Check → Vendor Validation
       ↓                                                         ↓
Categorize & Budget Check → Fraud Detection → Payment Optimization
       ↓                                                         ↓
Log to Tracker → Route for Approval → Slack Notification
```

### Step-by-Step Flow

| Step | Node | Description |
|------|------|-------------|
| 1 | **Gmail Trigger** | Watches for emails with "Invoice", "Bill", or "Payment Due" in subject |
| 2 | **Get Invoice Email** | Downloads the PDF attachment from the email |
| 3 | **PDF Vector Extract** | Uses AI to extract complete invoice data including PO numbers, payment terms, and line items |
| 4 | **Advanced Duplicate Check** | Generates multiple fingerprints to detect duplicate invoices |
| 5 | **Smart Vendor Validation** | Checks against approved vendor database, calculates risk scores |
| 6 | **Auto-Categorize & Budget Check** | Categorizes line items by keywords, tracks against monthly budgets |
| 7 | **Fraud Detection** | Flags suspicious patterns and assigns risk levels |
| 8 | **Payment Optimization** | Calculates early payment discounts and ROI |
| 9 | **Log to Invoice Tracker** | Saves comprehensive data to Google Sheets |
| 10 | **Approval Router** | Routes to auto-approval or manager/director review |

---

## Services Required

| Service | Purpose |
|---------|---------|
| **Gmail** | Email monitoring for incoming invoices |
| **PDF Vector** | AI-powered data extraction from invoice PDFs |
| **Google Sheets** | Invoice tracking and audit trail |
| **Slack** | Approval notifications and alerts |

---

## Fraud Detection Rules

The workflow automatically flags invoices with these suspicious patterns:

| Rule | Trigger Condition |
|------|-------------------|
| Round Numbers | Amounts ending in $X,000 over $5K |
| Rushed Payment | Due date less than 3 days from invoice date |
| Missing Address | No vendor address on invoices over $2K |
| Missing Tax ID | No tax ID on invoices over $5K |
| Suspicious Items | Line items containing gift cards, wire transfers, crypto, etc. |

**Risk Levels:**
- **Low** - No flags detected
- **Medium** - 1-2 flags detected
- **High** - 3+ flags detected (requires review)

---

## Approval Routing Logic

| Condition | Route To | Auto-Approve |
|-----------|----------|--------------|
| Approved vendor + Under limit + Has PO | Auto-Approved | Yes |
| Unknown vendor | Finance Manager | No |
| Exceeds vendor limit | Finance Director | No |
| Amount > $5K + Manual vendor | Finance Manager | No |
| No PO + Amount > $1K | Finance Manager | No |

---

## Who Is This For?

- **Finance Departments** in medium-to-large organizations
- **Accounts Payable Teams** needing approval workflows
- **Companies** requiring fraud detection and vendor validation
- **Organizations** with budget tracking requirements

---

## Quick Setup

1. **Import** the workflow JSON into your n8n instance
2. **Configure Gmail** OAuth credentials for email monitoring
3. **Set up Google Sheets** with columns for all tracked fields
4. **Configure Slack** with #finance channel for approvals
5. **Customize** the vendor database in "Smart Vendor Validation" node
6. **Adjust** budget thresholds and approval limits
7. **Activate** the workflow

---

## Download

[**Download Invoice Processing - AP Automation Workflow (JSON)**](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-approval.json)

**Right-click the link above and select "Save Link As..." to download, or click to view the JSON and copy/paste directly into n8n.**

---

## Customization Ideas

- **Vendor Database** - Add your approved vendors with custom spending limits
- **Fraud Rules** - Adjust detection rules for your industry
- **Approval Thresholds** - Configure dollar amounts for each approval level
- **ERP Integration** - Connect to your accounting system via API
- **Multi-Channel Alerts** - Add email notifications alongside Slack

---

## Data Extracted

The AI extracts these fields from each invoice:

```
Invoice
├── invoiceNumber
├── vendor
│   ├── name
│   ├── address
│   └── taxId
├── invoiceDate
├── dueDate
├── purchaseOrderNumber
├── billTo
├── lineItems[]
│   ├── description
│   ├── quantity
│   ├── unitPrice
│   ├── amount
│   └── category
├── subtotal
├── tax / taxRate
├── shipping
├── total
├── paymentTerms
└── currency
```

---

## Questions or Feedback?

If you have questions about this workflow or suggestions for improvements, please open an issue or discussion in this repository.

---

**Tags:** `n8n` `automation` `invoice-processing` `accounts-payable` `fraud-detection` `workflow` `finance` `ap-automation`
