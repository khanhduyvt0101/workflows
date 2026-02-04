# Awesome Document-Processing Automation Workflows

![n8n Workflows](https://img.shields.io/badge/n8n-29_workflows-FF6D5A)
![Zapier](https://img.shields.io/badge/Zapier-coming_soon-FF4A00)
![Make](https://img.shields.io/badge/Make.com-coming_soon-6E52FF)
![License](https://img.shields.io/badge/License-MIT-green)

> A curated collection of ready-to-use automation workflows for **PDF processing**, **document extraction**, and **intelligent document automation**.

Transform your document workflows with AI-powered automation. Extract data from invoices, process resumes, validate contracts, and more!

---

## Supported Platforms

| Platform | Status | Workflows | Folder |
|:--------:|:------:|:---------:|:------:|
| ![n8n](https://img.shields.io/badge/-n8n-FF6D5A?style=flat&logo=n8n&logoColor=white) | Available | 29 | [`n8n-workflows/`](n8n-workflows/) |
| ![Zapier](https://img.shields.io/badge/-Zapier-FF4A00?style=flat&logo=zapier&logoColor=white) | Coming Soon | - | [`zapier-workflows/`](zapier-workflows/) |
| ![Make](https://img.shields.io/badge/-Make.com-6E52FF?style=flat&logo=make&logoColor=white) | Coming Soon | - | [`make-workflows/`](make-workflows/) |

---

## n8n Workflows

> **About n8n**: These workflows are designed for [n8n](https://n8n.io/) - a fair-code workflow automation platform. You'll need an n8n instance (self-hosted or cloud) to use these workflows.

### Requirements

Before importing, ensure you have:
- An **n8n instance** (self-hosted or [n8n Cloud](https://n8n.io/cloud/))
- Relevant **credentials** configured (Google, Slack, etc.)

### Quick Start

1. **Right-click** the **Download** link → **"Save Link As..."** to save the workflow JSON file. Or click **Download** link and copy JSON content to your clipboard.
2. Open your n8n instance
3. Go to **Workflows** → **Import from File**
4. Select the downloaded JSON file
5. Configure your credentials in each node
6. Click **Activate** to start the workflow!

### Available Workflows

<details>
<summary><strong>📄 Invoice Data Extraction</strong> - Extract structured data from invoice PDFs | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-data-extraction.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/invoice-data-extraction.json">📋 Open</a></summary>

Perfect for finance teams, accountants, and small businesses who need to automate invoice processing. Drop invoices into a Google Drive folder and let AI extract all the key data automatically.

#### Who is this for?
- Finance teams processing high volumes of invoices
- Accountants needing structured invoice data
- Small businesses automating bookkeeping
- Anyone tired of manual data entry from PDFs

#### How it works
1. **Google Drive Trigger** watches your designated folder for new invoice files
2. **Download Invoice** retrieves the PDF from Google Drive
3. **PDF Vector Extract** uses AI to extract structured data: invoice number, vendor info, dates, line items with quantities and prices, subtotal, tax, and total
4. **Validate Invoice Data** checks if line items sum to subtotal and if total = subtotal + tax
5. **Log to Invoice Database** appends all extracted data to Google Sheets with validation status
6. **Conditional Notification** sends Slack alerts - success message for valid invoices, error alert for validation failures

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction)
- Google Sheets (data logging)
- Slack (notifications)

#### Setup instructions
1. Import the workflow JSON into n8n
2. Configure Google Drive credentials and set the folder path to your "Invoices" folder
3. Create a Google Sheet with columns: Invoice Number, Invoice Date, Due Date, Vendor, Customer, Subtotal, Tax, Total, Currency, Items, Status, Warnings, File Name, Processed Date
4. Configure the Google Sheets node with your spreadsheet ID
5. Set up Slack credentials and channel ID for notifications
6. Activate the workflow

#### Customizing this workflow
- Add additional validation rules (e.g., check vendor against approved list)
- Route high-value invoices to a separate approval workflow
- Connect to accounting software instead of Google Sheets
- Add email notifications alongside Slack

</details>

<details>
<summary><strong>💰 Invoice Processing & Approval</strong> - Enterprise invoice workflow with fraud detection | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-approval.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/invoice-processing-approval.json">📋 Open</a></summary>

A comprehensive invoice processing system with duplicate detection, vendor validation, budget tracking, fraud detection, and intelligent approval routing. Built for organizations that need enterprise-grade invoice management.

#### Who is this for?
- Finance departments in medium-to-large organizations
- Accounts payable teams needing approval workflows
- Companies requiring fraud detection and vendor validation
- Organizations with budget tracking requirements

#### How it works
1. **Gmail Trigger** watches for emails with "Invoice", "Bill", or "Payment Due" in subject
2. **Get Invoice Email** downloads the PDF attachment
3. **PDF Vector Extract** extracts complete invoice data including PO numbers, payment terms, and line item categories
4. **Advanced Duplicate Check** generates multiple fingerprints to detect duplicate invoices
5. **Smart Vendor Validation** checks against approved vendor database, calculates risk scores, and determines if PO exists
6. **Auto-Categorize & Budget Check** categorizes line items by keywords and tracks against monthly budgets
7. **Fraud Detection** flags suspicious patterns: round numbers over $5K, rushed payment windows, missing vendor details, suspicious items
8. **Payment Optimization** calculates early payment discounts and ROI
9. **Log to Invoice Tracker** saves comprehensive data to Google Sheets
10. **Approval Router** routes to auto-approval or manager/director review based on rules

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (invoice tracking)
- Slack (approval notifications)

#### Key features
- Multi-method duplicate detection
- Vendor risk scoring and limit checking
- Automatic line item categorization
- Budget warning alerts
- Fraud risk assessment
- Early payment discount calculations
- Smart approval routing (auto/manager/director)

#### Setup instructions
1. Import the workflow and configure Gmail OAuth credentials
2. Set up Google Sheets with comprehensive columns for all tracked fields
3. Configure Slack with appropriate channels (#finance for approvals)
4. Customize the vendor database in "Smart Vendor Validation" node
5. Adjust budget thresholds in "Auto-Categorize & Budget Check" node
6. Set approval thresholds based on your organization's policies

#### Customizing this workflow
- Modify vendor database with your approved vendors and limits
- Adjust fraud detection rules for your industry
- Change approval thresholds and routing logic
- Add integration with your ERP or accounting system
- Configure different Slack channels for different approval levels

</details>

<details>
<summary><strong>📧 Gmail Invoice Processor</strong> - Convert invoice PDFs to formatted Google Docs | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/gmail-invoice-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/gmail-invoice-processor.json">📋 Open</a></summary>

Automatically monitor your Gmail for invoice attachments and convert them into beautifully formatted Google Docs with markdown tables. Great for creating readable invoice records.

#### Who is this for?
- Freelancers tracking client invoices
- Small business owners who prefer Google Docs
- Anyone wanting readable invoice summaries
- Teams that share invoice information via Google Docs

#### How it works
1. **Gmail Trigger** monitors inbox for emails with attachments (every 5 minutes)
2. **PDF Vector Extract** uses AI to extract invoice number, vendor, date, total, and line items
3. **Format Invoice Markdown** creates a beautifully formatted markdown document with tables
4. **Create Document** creates a new Google Doc with the invoice title
5. **Update Document** inserts the formatted invoice content

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Docs (document creation)

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials
3. Configure Google Docs credentials
4. Optionally modify the Gmail filter to only watch specific labels
5. Activate the workflow

#### Customizing this workflow
- Add Google Drive folder organization for created docs
- Include email sender information in the document
- Add Slack notification when new doc is created
- Filter for specific senders or subject lines

</details>

<details>
<summary><strong>💰 Invoice Processing - AP Automation</strong> - Automate accounts payable with PO matching | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-ap-automation.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/invoice-processing-ap-automation.json">📋 Open</a></summary>

Complete accounts payable automation that extracts invoice data, validates calculations, matches against purchase orders, and routes invoices through approval workflows. Automatically catches overpayments and discrepancies before they become costly mistakes.

#### Who is this for?
- AP departments processing high volumes of invoices
- Finance teams needing PO matching and validation
- Controllers wanting to catch overpayments automatically
- Organizations requiring audit trails for invoice processing

#### How it works
1. **Gmail Trigger** monitors your invoice inbox for new emails every minute
2. **Gmail - Get Message** downloads the PDF attachment from the email
3. **Code - Rename Binary** prepares the attachment for PDF Vector processing
4. **PDF Vector - Extract Invoice** uses AI to extract all invoice fields: invoice number, dates, vendor info, PO number, line items with quantities and prices, subtotal, tax, and total
5. **Validate Invoice Data** checks if line items sum correctly, validates total calculations, and ensures required fields are present
6. **Sheets - PO Lookup** searches your PO Database for matching purchase order
7. **Code - Check PO Match** compares invoice total against PO amount with 2% tolerance
8. **IF - PO Match** routes invoices to Approved or Flagged paths
9. **Sheets - Log Approved/Flagged** records all invoice details with status to Invoice Log
10. **Gmail Notifications** sends confirmation to vendor (approved) or alert to AP team (flagged)

#### Services used
- Gmail (email monitoring & notifications)
- PDF Vector (AI extraction)
- Google Sheets (PO database & invoice logging)

#### Key features
- Automatic invoice data extraction from PDF attachments
- Line item validation (checks if amounts sum correctly)
- PO matching with 2% tolerance for minor variances
- Dual-path routing (Approved vs Flagged for review)
- Vendor confirmation emails for approved invoices
- AP team alerts for flagged invoices requiring review
- Complete audit trail in Google Sheets

#### Google Sheets structure
Create a spreadsheet with two tabs:

**Tab 1: PO Database**
| po_number | vendor_name | po_amount | po_date | status |
|-----------|-------------|-----------|---------|--------|

**Tab 2: Invoice Log**
| Invoice Number | Invoice Date | Due Date | Vendor | PO Number | Subtotal | Tax | Total | Items | Status | Warnings | Flag Reason | File Name | Processed Date |
|----------------|--------------|----------|--------|-----------|----------|-----|-------|-------|--------|----------|-------------|-----------|----------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your invoice inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create the Google Sheet with 'PO Database' and 'Invoice Log' tabs
5. Configure Google Sheets credentials and set the spreadsheet ID in all Sheets nodes
6. Update the AP team email address in the "Gmail - Alert Flagged" node
7. Activate the workflow

#### Real-world results
- 320 invoices/month processed automatically
- $47K in overpayments caught in year one
- 3 hours daily manual work reduced to 20 minutes exception review

#### Customizing this workflow
- Adjust PO tolerance percentage for your business needs
- Add Slack notifications alongside email alerts
- Connect to your ERP system instead of Google Sheets
- Add multi-level approval routing based on invoice amounts
- Include duplicate invoice detection

</details>

<details>
<summary><strong>💰 Invoice Processing with Validation</strong> - Extract and validate invoice math automatically | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-validation.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/invoice-processing-validation.json">📋 Open</a></summary>

Automated invoice processing that extracts data from PDF attachments, validates line item math, and routes invoices based on validation results. Valid invoices are logged and confirmed; invalid invoices are flagged for manual review.

#### Who is this for?
- Finance teams processing invoices via email
- Accounts payable departments needing validation
- Small businesses automating invoice intake
- Anyone wanting to catch math errors before payment

#### How it works
1. **Gmail Trigger** watches inbox every minute for new emails
2. **Get Invoice Attachment** downloads the PDF from the email
3. **Rename Binary to data** prepares attachment for PDF Vector processing
4. **PDF Vector Extract** uses AI to extract vendor info, invoice number, dates, line items (qty, price, amount), subtotal, tax, and total
5. **Validate Line Items** checks:
   - Line item math (quantity × unit_price = amount)
   - Subtotal matches sum of line items
   - Total = subtotal + tax
   - Required fields present (invoice number, vendor name, total)
6. **IF Valid?** routes based on validation result
7. **Valid path**: Log to "Invoices" sheet → Slack success notification
8. **Invalid path**: Log to "Flagged Invoices" sheet → Slack error notification

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (invoice logging)
- Slack (notifications)

#### Key features
- Line item calculation validation (qty × price = amount)
- Subtotal verification (sum of line items)
- Total calculation check (subtotal + tax = total)
- $0.01 tolerance for rounding differences
- Dual-path routing (valid vs needs review)
- Detailed error messages for flagged invoices
- Email subject tracking for context

#### Google Sheets structure
Create a spreadsheet with two tabs:

**Tab 1: Invoices**
| vendor_name | vendor_address | invoice_number | invoice_date | due_date | payment_terms | subtotal | tax_amount | total_amount | items_summary | validation_status | processed_at |
|-------------|----------------|----------------|--------------|----------|---------------|----------|------------|--------------|---------------|-------------------|--------------|

**Tab 2: Flagged Invoices**
| vendor_name | invoice_number | invoice_date | total_amount | error_count | errors | validation_status | processed_at | email_subject |
|-------------|----------------|--------------|--------------|-------------|--------|-------------------|--------------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your invoice inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create the Google Sheet with 'Invoices' and 'Flagged Invoices' tabs
5. Configure Google Sheets credentials and set the spreadsheet ID
6. Set up Slack credentials and configure channels (#invoices, #invoices-review)
7. Activate the workflow

#### Validation checks performed
- **Line item math**: quantity × unit_price should equal amount (±$0.01)
- **Subtotal check**: sum of line item amounts should equal stated subtotal
- **Total check**: subtotal + tax should equal total amount
- **Required fields**: invoice_number, vendor_name, total_amount must be present

#### Customizing this workflow
- Adjust validation tolerance for your business needs
- Add additional required field checks
- Connect to your accounting software instead of Google Sheets
- Add email notifications alongside Slack
- Include duplicate invoice detection

</details>

<details>
<summary><strong>💰 Tax Document Organizer</strong> - Auto-categorize and file tax documents | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/tax-document-organizer.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/tax-document-organizer.json">📋 Open</a></summary>

Automatically organize tax documents from email into categorized Google Drive folders. AI identifies document types (W-2, 1099, receipts) and files them by year and category.

#### Who is this for?
- Individuals preparing for tax season
- Accountants managing client documents
- Small businesses organizing financial records
- Anyone who receives tax documents via email

#### How it works
1. **Gmail Trigger** watches for new emails with attachments
2. **Get Message** downloads email with all attachments
3. **Split Attachments** processes each attachment separately (handles multi-attachment emails)
4. **PDF Vector Extract** identifies form type (W-2, 1099, receipt, etc.), tax year, taxpayer info, and amounts
5. **Categorize Document** assigns category (Income_Statements, Deductions, Tax_Returns, Other) and builds folder path
6. **File in Tax Folder** uploads to Google Drive with organized naming: `{Year}_{Category}_{FileName}`
7. **Update Tax Checklist** logs to Google Sheets for tracking

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Drive (file organization)
- Google Sheets (tracking checklist)

#### Folder structure created
```
Tax_Documents/
├── 2024/
│   ├── Income_Statements/   (W-2s, 1099s)
│   ├── Deductions/          (Receipts, 1098s)
│   ├── Tax_Returns/         (1040s)
│   └── Other/
└── 2023/
    └── ...
```

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail credentials
3. Create a root "Tax_Documents" folder in Google Drive
4. Configure Google Drive credentials and set the folder ID
5. Create a Google Sheet for the tax checklist
6. Activate the workflow

#### Customizing this workflow
- Add more document type categories
- Send notifications when documents are filed
- Create annual summary reports
- Add duplicate document detection

</details>

<details>
<summary><strong>💳 Expense Report Processor</strong> - Auto-categorize expenses with AI and route for approval | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/expense-report-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/expense-report-processor.json">📋 Open</a></summary>

Automatically process expense receipts with AI-powered data extraction, smart categorization based on merchant names, and intelligent approval routing for high-value expenses. Perfect for finance teams managing employee expenses.

#### Who is this for?
- Finance teams processing expense reports
- Employees submitting receipts for reimbursement
- Small businesses tracking company spending
- Managers needing visibility into team expenses

#### How it works
1. **Google Drive Trigger** monitors your "Expenses" folder for new receipt uploads
2. **Download Expense Document** retrieves the PDF/image from Google Drive
3. **PDF Vector Extract** uses AI to extract expense details: date, merchant, amount, category, payment method, tax, and line items
4. **Process & Categorize** auto-categorizes based on merchant keywords:
   - Travel: Uber, Lyft, airlines, hotels
   - Meals: restaurants, cafes, DoorDash
   - Office Supplies: Amazon, Staples, office stores
   - Software: SaaS, subscriptions
   - Also flags expenses >$500 for approval
5. **Log to Expense Tracker** appends all data to Google Sheets with receipt link
6. **Needs Approval?** routes based on amount threshold
7. **Request Approval** (>$500) sends Slack message with expense details and receipt link
8. **Confirm Logged** (≤$500) sends Slack confirmation of logged expense

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction)
- Google Sheets (expense tracking)
- Slack (notifications & approvals)

#### Expense categories
- Travel
- Meals
- Office Supplies
- Software
- Equipment
- Marketing
- Professional Services
- Utilities
- Other

#### Google Sheets structure
| Date | Merchant | Category | Amount | Currency | Tax | Payment Method | Description | Requires Approval | Receipt Link | Processed Date |
|------|----------|----------|--------|----------|-----|----------------|-------------|-------------------|--------------|----------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create an "Expenses" folder in Google Drive and configure the trigger
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack credentials and select your expense notification channel
7. Activate the workflow

#### Customizing this workflow
- Adjust the $500 approval threshold in the "Process & Categorize" node
- Add more merchant keywords for better auto-categorization
- Include additional expense categories
- Add email notifications alongside Slack
- Connect to your expense management system (Expensify, Concur, etc.)
- Add manager-specific approval routing based on department

</details>

<details>
<summary><strong>📦 Purchase Order Processor & Approval Workflow</strong> - Automate PO intake with smart approval routing | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/purchase-order-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/purchase-order-processor.json">📋 Open</a></summary>

Intelligent purchase order processing system that extracts PO data from email attachments, calculates approval levels based on amount thresholds, tracks urgency by delivery dates, and routes orders to appropriate approvers. Perfect for procurement and finance teams managing vendor orders.

#### Who is this for?
- Procurement teams managing vendor purchase orders
- Finance departments needing approval workflows
- Operations managers tracking order fulfillment
- Small to mid-size businesses automating PO processing

#### How it works
1. **Gmail Trigger** monitors inbox every minute for new PO emails
2. **Get a message** downloads the email with PDF attachment
3. **PDF Vector - Extract PO** uses AI to extract complete purchase order data:
   - PO number, order date, required delivery date
   - Vendor details (name, address, contact, email, phone)
   - Ship-to and bill-to addresses
   - Line items with item numbers, descriptions, quantities, unit prices, totals
   - Subtotal, shipping cost, tax, grand total
   - Payment terms and shipping method
4. **Process PO** calculates:
   - Internal tracking ID for reference
   - Line item count and formatted summary
   - Approval level based on amount thresholds
   - Urgency based on delivery date (Urgent: ≤3 days, High: ≤7 days, Normal: >7 days)
5. **Log to PO Tracker** appends all data to Google Sheets with status tracking
6. **Notify Procurement** sends Slack notification with PO details and approval requirements

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (PO tracking database)
- Slack (procurement notifications)

#### Approval thresholds
- **< $1,000**: Auto-approve (System)
- **$1,000 - $4,999**: Manager Approval
- **$5,000 - $24,999**: Director Approval
- **≥ $25,000**: VP/CFO Approval

#### Urgency levels
- **Urgent**: Required delivery in ≤3 days
- **High**: Required delivery in 4-7 days
- **Normal**: Required delivery in >7 days

#### Google Sheets structure
| Tracking ID | PO Number | Vendor | Order Date | Required Date | Line Items | Subtotal | Shipping | Tax | Grand Total | Approval Level | Urgency | Status | Received Date |
|-------------|-----------|--------|------------|---------------|------------|----------|----------|-----|-------------|----------------|---------|--------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your PO inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and set the spreadsheet ID
6. Set up Slack credentials and select your procurement notification channel
7. Activate the workflow

#### Customizing this workflow
- Adjust approval thresholds to match your organization's policies
- Add additional approval tiers or custom routing logic
- Include vendor validation against approved vendor list
- Add budget tracking and spend analytics
- Route to specific approvers based on department or category
- Send email notifications to approvers instead of Slack
- Integrate with ERP or procurement systems
- Add duplicate PO detection

</details>

<details>
<summary><strong>🏦 Bank Statement Analyzer</strong> - Auto-categorize spending and track savings rate | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/bank-statement-analyzer.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/bank-statement-analyzer.json">📋 Open</a></summary>

Automatically analyze bank statements with AI-powered transaction extraction, spending categorization, savings rate calculation, and monthly summary reports. Perfect for personal finance tracking and budget analysis.

#### Who is this for?
- Individuals tracking personal finances
- Small business owners monitoring expenses
- Freelancers managing business accounts
- Anyone wanting automated budget insights

#### How it works
1. **Gmail Trigger** monitors inbox for bank statement emails every minute
2. **Get Statement Email** downloads the PDF attachment
3. **PDF Vector Extract** uses AI to extract all transactions with:
   - Date, description, amount (positive for deposits, negative for withdrawals)
   - Running balance for each transaction
   - Smart categorization based on merchant names
4. **Analyze Spending** calculates:
   - Total income and spending
   - Savings rate percentage
   - Spending breakdown by category
   - Identifies large transactions (>$500)
5. **Log Monthly Summary** appends key metrics to Google Sheets
6. **Send Analysis Report** posts comprehensive summary to Slack

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (summary logging)
- Slack (monthly reports)

#### Spending categories
- Income
- Utilities
- Groceries
- Dining
- Shopping
- Transport
- Travel
- Subscriptions
- Healthcare
- Entertainment
- Transfer
- Other

#### Category rules
| Category | Merchants/Keywords |
|----------|-------------------|
| Travel | Airlines (DELTA, UNITED, AMERICAN), Hotels (HILTON, MARRIOTT, HYATT), Airbnb, Booking.com |
| Transport | UBER, LYFT, Gas stations (SHELL, CHEVRON, BP), Parking |
| Subscriptions | NETFLIX, SPOTIFY, ADOBE, APPLE.COM, recurring services |
| Groceries | WHOLE FOODS, TRADER JOE'S, COSTCO, PUBLIX, supermarkets |
| Dining | Restaurants, STARBUCKS, MCDONALD'S, DOORDASH, UBER EATS |
| Shopping | AMAZON, TARGET, BEST BUY, WALMART, retail stores |
| Utilities | Electric, gas, water, AT&T, COMCAST, VERIZON |
| Healthcare | CVS, WALGREENS, doctors, PLANET FITNESS |
| Entertainment | AMC, concerts, streaming, games |

#### Google Sheets structure
| Period Start | Period End | Opening Balance | Closing Balance | Total Income | Total Spending | Savings Rate % | Transaction Count | Processed Date |
|--------------|------------|-----------------|-----------------|--------------|----------------|----------------|-------------------|----------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your bank statement inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the "Monthly Summaries" tab and columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack credentials and select your finance notification channel
7. Activate the workflow

#### Slack report includes
- Statement period dates
- Total income and spending
- Savings rate percentage
- Spending breakdown by category with percentages
- List of large transactions (>$500)

#### Customizing this workflow
- Adjust the $500 threshold for large transaction alerts
- Add more merchant keywords for better categorization
- Connect to your budgeting app (YNAB, Mint) instead of Google Sheets
- Add email notifications alongside Slack
- Create weekly spending alerts instead of monthly summaries
- Add budget limit warnings for specific categories

</details>

<details>
<summary><strong>🧾 Receipt Scanner & Tax Organizer</strong> - Scan receipts and build tax deduction tracker | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/receipt-scanner-tax-organizer.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/receipt-scanner-tax-organizer.json">📋 Open</a></summary>

Automatically process receipts with AI-powered extraction, identify tax-deductible expenses, and organize by quarter/year. Perfect for freelancers and small business owners preparing for tax season.

#### Who is this for?
- Freelancers tracking business expenses
- Small business owners managing receipts
- Self-employed individuals preparing for taxes
- Anyone needing organized tax deduction records

#### How it works
1. **Google Drive Trigger** monitors your receipts folder for new uploads
2. **Download file** retrieves the receipt from Google Drive
3. **PDF Vector Extract** uses AI to extract receipt details: store name, date, items with prices, subtotal, tax, total, payment method, and determines if tax-deductible
4. **Process Receipt** generates unique receipt ID, calculates tax year and quarter, formats items for storage
5. **Log to Receipt Database** appends all receipt data to Google Sheets
6. **Tax Deductible?** checks if the receipt is marked as tax-deductible
7. **Add to Tax Deductions** (deductible path) logs to separate Tax Deductions sheet for easy tax prep

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction)
- Google Sheets (receipt database & tax deductions)

#### Tax deduction categories
- Office Supplies
- Business Meals
- Travel
- Equipment
- Software
- Professional Services
- Marketing
- Not Deductible

#### Google Sheets structure
Create a spreadsheet with two tabs:

**Tab 1: Receipt Database**
| Receipt ID | Date | Store | Items | Subtotal | Tax | Total | Payment | Tax Deductible | Deduction Category | Tax Year | Quarter |
|------------|------|-------|-------|----------|-----|-------|---------|----------------|-------------------|----------|---------|

**Tab 2: Tax Deductions**
| Receipt ID | Date | Vendor | Amount | Category | Tax Year | Quarter |
|------------|------|--------|--------|----------|----------|---------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Receipts" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with 'Receipt Database' and 'Tax Deductions' tabs
5. Configure Google Sheets credentials and set the spreadsheet ID in both Sheets nodes
6. Activate the workflow

#### Key features
- Unique receipt ID generation (RCP-XXXXX format)
- Automatic tax year and quarter calculation
- AI-powered tax deductibility assessment
- Categorized deduction tracking
- Organized by tax year for easy annual reporting

#### Customizing this workflow
- Add Slack notifications when receipts are processed
- Integrate with accounting software (QuickBooks, FreshBooks)
- Add monthly/quarterly summary reports
- Include receipt image storage with Google Drive links
- Add duplicate receipt detection
- Create annual tax deduction exports

</details>

<details>
<summary><strong>🏥 Insurance Pre-Authorization</strong> - Process prior auth requests with emergency fast-tracking | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/insurance-pre-authorization.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/insurance-pre-authorization.json">📋 Open</a></summary>

Automate insurance prior authorization processing with emergency triage, coverage validation, and intelligent routing. Emergency requests are auto-approved and fast-tracked.

#### Who is this for?
- Healthcare utilization review teams
- Insurance companies processing authorizations
- Medical practices submitting prior auth requests
- Healthcare administrators managing approvals

#### How it works
1. **Gmail Trigger** watches for emails with "Prior Authorization" in subject
2. **Get Auth Request Email** downloads the PDF attachment
3. **PDF Vector Extract** extracts patient info, insurance details, provider info, procedure codes, diagnosis codes, and clinical justification
4. **Emergency Triage** checks if request is marked as emergency
5. **Fast-Track Emergency** (emergency path) auto-approves and generates immediate notification
6. **Full Validation** (standard path) validates coverage, checks required fields, determines if peer review needed
7. **Log Authorization** saves to tracking spreadsheet
8. **Requires Review?** routes based on validation results
9. **Slack Notifications** send appropriate alerts (Emergency Approved, Needs Review, or Auto-Approved)

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (authorization tracking)
- Slack (review notifications)

#### Key features
- Emergency request auto-approval
- Coverage date validation
- Missing information detection
- Peer review flagging for high-cost procedures
- Priority assignment (Emergency/Urgent/High/Standard)
- Comprehensive audit trail

#### Setup instructions
1. Import the workflow and configure Gmail OAuth
2. Set up Google Sheets with authorization tracking columns
3. Configure Slack with #utilization-review channel
4. Adjust high-cost threshold and auth-required procedure list as needed
5. Activate the workflow

#### Customizing this workflow
- Modify procedure codes that require authorization
- Adjust cost thresholds for different plan types
- Add integration with your authorization management system
- Configure additional validation rules for your payers

</details>

<details>
<summary><strong>🏥 Insurance Claim Document Processor</strong> - Automate insurance claim processing with routing and reimbursement estimates | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/insurance-claim-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/insurance-claim-processor.json">📋 Open</a></summary>

Comprehensive insurance claim processing workflow that extracts claim data from email attachments, calculates estimated reimbursement, routes claims based on amount thresholds, and flags missing pre-authorizations or documentation. Perfect for insurance companies automating claims intake.

#### Who is this for?
- Insurance companies processing claims
- Healthcare billing departments
- Claims adjusters and reviewers
- Medical billing professionals

#### How it works
1. **Gmail Trigger** monitors inbox for new claim emails with attachments every minute
2. **Get a message** downloads the email with claim PDF attachment
3. **PDF Vector - Extract Claim** uses AI to extract comprehensive claim data:
   - Claim type (Medical, Auto, Property, Life, Disability, Travel)
   - Policy number and claim number
   - Claimant information (name, policy holder, relationship, DOB, contact)
   - Incident date, description, and location
   - Provider details (name, NPI, address)
   - Diagnosis codes and descriptions
   - Procedures with codes, descriptions, and amounts
   - Total amount, deductible, co-payment
   - Pre-authorization number
   - Supporting documents list
4. **Process Claim** enriches and validates claim data:
   - Generates unique claim ID if not present (CLM-XXXXX format)
   - Calculates estimated reimbursement (Total - Deductible - Copay)
   - Formats procedure and diagnosis lists
   - Routes claims based on amount:
     - ≤$1,000: Auto-Approve
     - $1,001-$5,000: Claims Adjuster
     - >$5,000: Senior Adjuster
   - Flags claims for:
     - Missing Pre-Authorization (if amount >$500)
     - No Supporting Documents attached
5. **Log Claim** appends all claim details to Google Sheets tracking database
6. **Notify Claims Team** sends formatted Slack notification with:
   - Claim ID, type, and policy number
   - Claimant name and incident date
   - Financial summary (total claimed, deductible, estimated reimbursement)
   - Routing recommendation
   - Any flags requiring attention

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (claim tracking)
- Slack (team notifications)

#### Claim types supported
- Medical/Health
- Auto/Vehicle
- Property/Home
- Life Insurance
- Disability
- Travel Insurance

#### Routing thresholds
| Amount Range | Routed To | Approval Level |
|--------------|-----------|----------------|
| ≤ $1,000 | Auto-Approve | Automatic |
| $1,001 - $5,000 | Claims Adjuster | Standard Review |
| > $5,000 | Senior Adjuster | Senior Review |

#### Auto-flagged issues
- **Missing Pre-Authorization** - Flagged when amount >$500 and no pre-auth number present
- **No Supporting Documents** - Flagged when no supporting documents attached

#### Google Sheets structure
| Claim ID | Claim Type | Policy Number | Claimant | Incident Date | Provider | Diagnosis | Total Amount | Deductible | Est. Reimbursement | Route To | Flags | Status | Received Date |
|----------|------------|---------------|----------|---------------|----------|-----------|--------------|------------|-------------------|----------|-------|--------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your claims inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and set the spreadsheet ID in the "Log Claim" node
6. Set up Slack OAuth credentials and select your claims team channel
7. Activate the workflow

#### Key features
- Automatic claim ID generation (CLM-XXXXX format)
- Reimbursement estimation (Total - Deductible - Copay)
- Intelligent routing based on claim amount
- Pre-authorization validation for high-value claims
- Supporting documentation checks
- Formatted diagnosis and procedure lists
- Complete audit trail in Google Sheets

#### Customizing this workflow
- Adjust routing thresholds in the "Process Claim" node (currently $1K and $5K)
- Modify pre-authorization threshold (currently $500) for your organization's policies
- Add additional claim types to the extraction schema
- Connect to your claims management system instead of Google Sheets
- Add email auto-replies to claimants confirming receipt
- Include duplicate claim detection based on claim number or policy
- Add approval workflow integration for flagged claims
- Create separate Slack channels for different claim types or routing levels

</details>

<details>
<summary><strong>🏥 Medical Records Intake</strong> - Automate patient intake form processing | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/medical-records-intake.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/medical-records-intake.json">📋 Open</a></summary>

Streamline patient intake by automatically extracting data from intake forms, adding to your patient database, and sending appropriate follow-up emails based on form completeness.

#### Who is this for?
- Medical practices processing new patients
- Healthcare clinics with email-based intake
- Administrative staff managing patient records
- Telehealth providers collecting patient information

#### How it works
1. **Gmail Trigger** watches for emails with PDF attachments
2. **Get Message** downloads the email and attachments
3. **Prepare Binary** normalizes attachment format for processing
4. **PDF Vector Extract** extracts patient name, DOB, contact info, insurance details, emergency contact, medications, allergies, and medical history
5. **Add to Patient Database** appends patient record to Google Sheets
6. **Is Complete?** checks if required fields (name, DOB, insurance) are present
7. **Send Welcome Email** (complete) sends confirmation to patient
8. **Request Complete Info** (incomplete) notifies sender of missing fields

#### Services used
- Gmail (email monitoring & sending)
- PDF Vector (AI extraction)
- Google Sheets (patient database)

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials
3. Create a Google Sheet for patient database with columns: Patient Name, Date of Birth, Phone, Email, Insurance Provider, Policy Number, Emergency Contact, Emergency Phone, Medications, Allergies, Intake Date
4. Configure the spreadsheet ID in the Google Sheets node
5. Activate the workflow

#### Customizing this workflow
- Add HIPAA-compliant storage integration
- Connect to your EHR/EMR system
- Add appointment scheduling follow-up
- Include insurance verification step

</details>

<details>
<summary><strong>🏥 Patient Intake Form Processor</strong> - Process healthcare intake forms with allergy alerts | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/patient-intake-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/patient-intake-processor.json">📋 Open</a></summary>

HIPAA-compliant patient intake form processor that extracts demographics, insurance, medical history, medications, and allergies from uploaded forms. Automatically creates patient records and sends critical allergy alerts to medical staff.

#### Who is this for?
- Medical practices processing new patient intake forms
- Healthcare clinics automating patient registration
- Urgent care facilities needing quick patient data entry
- Telehealth providers collecting patient information

#### How it works
1. **Google Drive Trigger** monitors your intake forms folder for new uploads
2. **Download File** retrieves the PDF intake form from Google Drive
3. **PDF Vector - Extract Intake** uses AI to extract comprehensive patient data:
   - Patient demographics (name, DOB, gender, contact info)
   - Insurance information (provider, policy, group number)
   - Medical history (conditions, surgeries, family history)
   - Current medications (name, dosage, frequency)
   - Allergies with reaction severity
   - Emergency contact details
   - Reason for visit
4. **Process Intake Data** generates unique patient ID, calculates age, formats data, and detects critical allergies
5. **Create Patient Record** appends patient data to Google Sheets database
6. **Critical Allergy?** checks if patient has critical allergies (penicillin, sulfa, latex, iodine)
7. **Critical Alert** (if allergies detected) sends urgent Slack alert to medical staff
8. **Notify Front Desk** (standard path) sends new patient notification to front desk

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction)
- Google Sheets (patient database)
- Slack (staff notifications & allergy alerts)

#### Critical allergens detected
- Penicillin
- Sulfa drugs
- Latex
- Iodine
- Aspirin
- NSAIDs

#### Data fields extracted
| Category | Fields |
|----------|--------|
| Demographics | First name, last name, DOB, gender, SSN (last 4), phone, email, address |
| Insurance | Provider, policy number, group number, subscriber name, relationship |
| Medical History | Conditions, past surgeries, family history |
| Medications | Name, dosage, frequency for each medication |
| Allergies | Allergen name, reaction/severity for each allergy |
| Emergency Contact | Name, relationship, phone number |

#### Google Sheets structure
| Patient ID | Name | DOB | Age | Gender | Phone | Email | Insurance | Conditions | Medications | Allergies | Reason for Visit | Emergency Contact | Intake Date |
|------------|------|-----|-----|--------|-------|-------|-----------|------------|-------------|-----------|------------------|-------------------|-------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Patient Intake Forms" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack OAuth credentials and configure two channels:
   - #medical-alerts for critical allergy notifications
   - #front-desk for standard intake notifications
7. Activate the workflow

#### HIPAA compliance notes
- Self-host n8n in a secure, compliant environment
- Ensure all connections use TLS encryption
- Restrict access to authorized personnel only
- Enable audit logging for all workflow executions
- Consider encrypting data at rest in Google Sheets
- Review your BAA agreements with all service providers

#### Key features
- Automatic patient ID generation (PT-XXXXXX format)
- Age calculation from date of birth
- Critical allergy detection and urgent alerts
- NKDA (No Known Drug Allergies) default for patients without allergies
- Formatted medication and allergy lists
- Emergency contact information capture

#### Customizing this workflow
- Add more critical allergens to the detection list in the "Process Intake Data" node
- Connect to your EHR/EMR system instead of Google Sheets
- Add appointment scheduling follow-up
- Include insurance verification via API
- Add email notifications alongside Slack
- Create separate alert channels for different allergy severity levels
- Add duplicate patient detection based on DOB and name

</details>

<details>
<summary><strong>⚖️ NDA Compliance Checker</strong> - Validate NDAs for required clauses and risk | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/nda-compliance-checker.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/nda-compliance-checker.json">📋 Open</a></summary>

Automatically analyze NDA documents for compliance with required clauses, calculate risk scores, and route alerts based on risk level. Perfect for legal teams reviewing contracts.

#### Who is this for?
- Legal departments reviewing NDAs
- Contract managers ensuring compliance
- Business development teams evaluating agreements
- Compliance officers tracking NDA terms

#### How it works
1. **Google Drive Trigger** watches NDA folder for new documents
2. **Download NDA** retrieves the PDF file
3. **PDF Vector Extract** extracts parties, dates, terms, scope, obligations, remedies, governing law, and special provisions
4. **Check NDA Compliance** evaluates 7 required clauses, calculates compliance score, identifies risk factors, determines expiration status
5. **Log to NDA Register** saves analysis to tracking spreadsheet
6. **Route by Risk Level** directs to appropriate Slack channel
7. **Risk-Based Alerts** sends detailed notifications:
   - High Risk → #legal-urgent (DO NOT EXECUTE warning)
   - Medium Risk → #legal (Review Recommended)
   - Low Risk → #general (Logged Successfully)

#### Services used
- Google Drive (file monitoring)
- PDF Vector (AI extraction)
- Google Sheets (NDA register)
- Slack (risk-based alerts)

#### 7-Point compliance checklist
1. Definition of Confidential Information
2. Permitted Disclosures
3. Exclusions from Confidentiality
4. Return of Materials
5. Remedies for Breach
6. Governing Law
7. Term/Duration

#### Risk factors detected
- No breach remedies specified
- No injunctive relief clause
- No exclusions defined (may be unenforceable)
- One-way NDA (limited protection)
- No governing law specified

#### Setup instructions
1. Import the workflow into n8n
2. Create an "NDAs" folder in Google Drive
3. Configure Google Drive credentials and folder ID
4. Set up Google Sheets for NDA register
5. Configure Slack with appropriate channels for each risk level
6. Activate the workflow

#### Customizing this workflow
- Add your organization's required clauses
- Modify risk scoring thresholds
- Include automatic legal team assignment
- Add expiration reminder notifications

</details>

<details>
<summary><strong>📝 AI Contract Review & Risk Analysis</strong> - Analyze contracts for risks and key terms | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/contract-review-risk-analysis.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/contract-review-risk-analysis.json">📋 Open</a></summary>

Automatically review contracts with AI-powered extraction of key terms, risk identification, and executive summary generation. Perfect for legal teams and business operations needing to streamline contract review processes.

#### Who is this for?
- Legal teams reviewing contracts
- Business operations managing vendor agreements
- Procurement departments evaluating supplier contracts
- Sales operations reviewing customer contracts

#### How it works
1. **Google Drive Trigger** monitors your contracts folder for new uploads
2. **Download Contract** retrieves the PDF from Google Drive
3. **PDF Vector - Analyze Contract** uses AI to extract structured data:
   - Contract type (Service Agreement, NDA, Lease, etc.)
   - Parties involved with roles
   - Effective and expiration dates
   - Contract value and payment terms
   - Auto-renewal and termination clauses
   - Liability limitations and indemnification
   - Risk flags with severity levels (High/Medium/Low)
4. **PDF Vector - Executive Summary** generates a brief summary with top concerns and overall risk rating
5. **Compile Review** aggregates all data, counts risks by severity, and determines review status
6. **Log Contract Review** appends comprehensive analysis to Google Sheets
7. **Send Review Report** posts detailed Slack notification with:
   - Contract details and parties
   - Executive summary
   - Risk assessment counts
   - List of identified risks
   - Review status recommendation
   - Direct link to contract

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction & analysis)
- Google Sheets (contract tracking)
- Slack (review notifications)

#### Risk severity levels
- **High** - Requires legal review before signing
- **Medium** - Review recommended
- **Low** - Ready for signature

#### Risk flags detected
- Unusual liability clauses
- Missing standard protections
- One-sided indemnification
- Unfavorable termination terms
- Auto-renewal traps
- Non-compete restrictions
- Confidentiality concerns

#### Contract types supported
- Service Agreements
- Employment Contracts
- NDAs
- Lease Agreements
- Sales Contracts
- Partnership Agreements
- License Agreements

#### Google Sheets structure
| File Name | Contract Type | Parties | Effective Date | Expiration Date | Value | Auto Renewal | Termination Notice | High Risks | Medium Risks | Review Status | Contract Link | Reviewed Date |
|-----------|---------------|---------|----------------|-----------------|-------|--------------|-------------------|------------|--------------|---------------|---------------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Contracts" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack OAuth credentials and select your #contract-reviews channel
7. Activate the workflow

#### Review status logic
- **Requires Legal Review** - Any high-risk flags detected
- **Review Recommended** - 2 or more medium-risk flags
- **Ready for Signature** - Low risk, standard terms

#### Customizing this workflow
- Add additional contract types to the extraction schema
- Modify risk assessment criteria in the Compile Review node
- Route high-risk contracts to specific legal team members
- Add email notifications alongside Slack
- Integrate with your CLM (Contract Lifecycle Management) system
- Add expiration date reminders and renewal tracking
- Include contract comparison against your standard templates

</details>

<details>
<summary><strong>🏠 Mortgage Application Validator</strong> - Validate applications with DTI/LTV calculations | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/mortgage-application-validator.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/mortgage-application-validator.json">📋 Open</a></summary>

Comprehensive mortgage application processing with automatic DTI and LTV calculations, credit score routing, and risk assessment. Routes applications to different channels based on credit tier.

#### Who is this for?
- Mortgage lenders and brokers
- Loan officers processing applications
- Underwriting teams evaluating risk
- Financial institutions automating intake

#### How it works
1. **Gmail Trigger** watches for emails with "Mortgage Application" in subject
2. **Get Application Email** downloads the PDF attachment
3. **PDF Vector Extract** extracts borrower info, employment, income, assets, liabilities, property details, and loan terms
4. **Calculate DTI & Validate** performs comprehensive analysis:
   - Calculates monthly payment (principal + interest)
   - Adds property tax and insurance estimates
   - Computes front-end DTI (housing/income)
   - Computes back-end DTI (total debt/income)
   - Calculates LTV ratio
   - Checks reserves (months of payments in assets)
   - Identifies qualification issues
5. **Log to Application Database** saves to Google Sheets
6. **Route by Credit Score** directs to appropriate channel:
   - Excellent (740+) → Fast-track approval
   - Good (670-739) → Standard approval
   - Fair (620-669) → Additional docs required
   - Poor (<620) → Manual underwriting
   - No Score → Incomplete application

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (application tracking)
- Slack (4 routing channels)

#### Qualification checks performed
- DTI ratio (max 43% back-end, 28% front-end)
- LTV ratio (flags >80% for PMI, >95% for review)
- Credit score minimums (620)
- Employment history (2+ years preferred)
- Reserve requirements (2+ months)
- Bankruptcy/foreclosure history

#### Setup instructions
1. Import the workflow and configure Gmail OAuth
2. Create Google Sheet for applications database
3. Configure 4 Slack channels: #mortgage-approvals, #mortgage-underwriting (2x), one for incomplete
4. Adjust qualification thresholds as needed
5. Activate the workflow

#### Customizing this workflow
- Modify credit score tier thresholds
- Adjust DTI and LTV limits
- Add integration with credit bureaus
- Connect to your loan origination system
- Add automated applicant emails

</details>

<details>
<summary><strong>🎓 Education Transcript Processor</strong> - Process transcripts with GPA analysis | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/education-transcript-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/education-transcript-processor.json">📋 Open</a></summary>

Extract and analyze academic transcripts with GPA calculation, academic standing determination, and automated verification. Great for admissions offices and HR departments.

#### Who is this for?
- University admissions offices
- HR departments verifying education
- Scholarship committees reviewing applications
- Credential verification services

#### How it works
1. **Gmail Trigger** watches for emails with "Transcript" or "Academic Record" in subject
2. **Get Transcript Email** downloads the PDF attachment
3. **PDF Vector Extract** extracts student info, institution, courses with grades, GPA, degree info, and honors
4. **Analyze Transcript** processes the data:
   - Counts courses and calculates credits
   - Creates grade distribution
   - Categorizes GPA (Exceptional/Excellent/Good/Fair/Below Average/Poor)
   - Determines academic standing (Dean's List, Good Standing, or Probation)
   - Checks if verification is needed
5. **Log to Transcript Database** saves to Google Sheets
6. **Verify with School?** checks if official transcript with student ID
7. **Simple Verification Check** performs 6-point verification:
   - Official transcript status
   - Student ID present
   - Valid GPA range (0-4.0)
   - Institution identified
   - Courses present
   - Graduation date (if applicable)
8. **Slack Notifications** send verified or manual review alerts

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (transcript database)
- Slack (verification alerts)

#### GPA categories
- 3.8+ = Exceptional
- 3.5-3.79 = Excellent
- 3.0-3.49 = Good
- 2.5-2.99 = Fair
- 2.0-2.49 = Below Average
- <2.0 = Poor (Academic Probation)

#### Setup instructions
1. Import the workflow and configure Gmail OAuth
2. Create Google Sheet for transcript database
3. Configure Slack with #admissions channel
4. Activate the workflow

#### Customizing this workflow
- Integrate with National Student Clearinghouse API
- Add specific degree program requirements
- Connect to your student information system
- Add duplicate detection for re-submissions

</details>

<details>
<summary><strong>👤 Resume Parser & Scoring</strong> - Parse and score candidates automatically | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/resume-parser.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/resume-parser.json">📋 Open</a></summary>

Automated resume processing with AI extraction, 100-point scoring system, and recruiter notifications. Drop resumes in Google Drive and get scored candidates in your spreadsheet.

#### Who is this for?
- HR departments and recruiters
- Hiring managers screening candidates
- Staffing agencies processing applications
- Anyone handling high volumes of resumes

#### How it works
1. **Google Drive Trigger** watches "Resumes" folder for new files
2. **Download Resume** retrieves the file from Google Drive
3. **PDF Vector Parse** extracts name, contact info, work experience with dates, education, technical skills, soft skills, certifications, and languages
4. **Score Candidate** calculates 100-point score:
   - Experience (40 pts max): 0-2 yrs = 10, 2-5 yrs = 25, 5+ yrs = 40
   - Education (30 pts max): PhD = 30, Masters = 25, Bachelors = 20, Other = 10
   - Skills Match (30 pts max): 3 points per matched skill
5. **Merge Binary Data** combines score data with original resume
6. **PDF Vector AI Assessment** generates qualitative assessment including strengths, suitable roles, and seniority level
7. **Log to Candidate Database** saves everything to Google Sheets with direct resume link
8. **Notify Recruiter** sends Slack alert with score breakdown

#### Services used
- Google Drive (file monitoring)
- PDF Vector (AI extraction & assessment)
- Google Sheets (candidate database)
- Slack (recruiter notifications)

#### Scoring breakdown (100 points total)
- **Experience (40 pts)**: Years of work experience calculated from dates
- **Education (30 pts)**: Highest degree achieved
- **Skills Match (30 pts)**: Technical skills matching job requirements

#### Default skills to match (customizable)
JavaScript, Python, React, Node.js, SQL, API, Git, AWS, Docker

#### Status assignment
- 75+ = "Strong Candidate - Schedule Interview"
- 50-74 = "Potential - Review Further"
- <50 = "Not a Match"

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Resumes" folder in Google Drive
3. Configure Google Drive credentials and folder path
4. Create Google Sheet with columns: Candidate Name, Email, Phone, Location, Years Experience, Score, Status, Experience/Education/Skills Scores, Skills Matched, Experience, Education, Skills, LinkedIn, AI Assessment, File Name, Resume Link, Resume File ID, Processed Date
5. Configure Slack channel for recruiter notifications
6. Activate the workflow

#### Customizing this workflow
- Modify required skills list for different positions
- Adjust scoring weights for your priorities
- Add job requisition matching
- Include automated candidate emails
- Connect to your ATS (Applicant Tracking System)

</details>

<details>
<summary><strong>📋 Job Application Processor & Candidate Scorer</strong> - Process applications with AI scoring and auto-replies | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/job-application-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/job-application-processor.json">📋 Open</a></summary>

End-to-end job application processing with AI-powered resume parsing, 100-point candidate scoring, automatic ATS logging, candidate auto-replies, and HR team notifications via Slack. Perfect for streamlining your recruiting pipeline.

#### Who is this for?
- HR departments processing job applications
- Recruiters managing candidate pipelines
- Hiring managers screening applicants
- Staffing agencies handling high volumes of applications

#### How it works
1. **Gmail Trigger** monitors inbox for job application emails every minute
2. **Get a message** downloads the email with resume attachment
3. **Prepare Binary File** normalizes attachment format for PDF Vector processing
4. **PDF Vector - Parse Resume** uses AI to extract comprehensive candidate data:
   - Full name, email, phone, location
   - LinkedIn profile URL
   - Years of experience and current title
   - Work history with companies, titles, dates, and achievements
   - Education with degrees and institutions
   - Technical skills, soft skills, certifications
   - Languages spoken
5. **Score Candidate** calculates 100-point score:
   - Experience (40 pts): 7+ yrs = 40, 5-6 yrs = 35, 3-4 yrs = 25, 1-2 yrs = 15, <1 yr = 5
   - Education (30 pts): PhD = 30, Masters = 25, Bachelors = 20, Other = 10
   - Skills Match (30 pts): 3 points per matched required skill
6. **Add to ATS** logs candidate data to Google Sheets with score and status
7. **Send Auto-Reply** sends professional acknowledgment email to candidate
8. **Notify HR Team** posts Slack notification with candidate summary and score

#### Services used
- Gmail (email monitoring & auto-replies)
- PDF Vector (AI resume parsing)
- Google Sheets (ATS database)
- Slack (HR notifications)

#### Scoring breakdown (100 points total)
| Component | Max Points | Criteria |
|-----------|------------|----------|
| Experience | 40 | Years of professional experience |
| Education | 30 | Highest degree achieved |
| Skills Match | 30 | Technical skills matching job requirements |

#### Default required skills (customizable)
JavaScript, Python, React, Node.js, SQL, API, Git, AWS, Docker, TypeScript

#### Status assignment
- **75+ = Schedule Interview** - Strong candidate, prioritize
- **50-74 = Review Further** - Potential fit, needs evaluation
- **<50 = Pass** - Not a match for current requirements

#### Google Sheets structure
| Name | Email | Phone | Location | Current Title | Years Experience | Score | Status | Skills | Skills Matched | Application Date | Processed Date |
|------|-------|-------|----------|---------------|------------------|-------|--------|--------|----------------|------------------|----------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your job application inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and set the spreadsheet ID
6. Set up Slack OAuth credentials and select your HR/recruiting channel
7. Customize required skills in the "Score Candidate" node for your position
8. Activate the workflow

#### Key features
- AI-powered resume parsing with structured data extraction
- Configurable skills matching for different positions
- Automatic candidate scoring with transparent breakdown
- Professional auto-reply emails to candidates
- Real-time Slack notifications for HR team
- Complete audit trail in Google Sheets ATS

#### Customizing this workflow
- Modify the required skills list for different job positions
- Adjust scoring weights in the "Score Candidate" node
- Add Gmail filters to only process specific subject lines (e.g., "Application for Software Engineer")
- Connect to your existing ATS instead of Google Sheets
- Add conditional routing based on score (e.g., high scorers to fast-track channel)
- Include LinkedIn profile lookup for additional candidate data
- Add interview scheduling automation for high-scoring candidates

</details>

<details>
<summary><strong>👋 Employee Onboarding Document Processor</strong> - Automate HR onboarding with compliance checks | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/employee-onboarding-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/employee-onboarding-processor.json">📋 Open</a></summary>

Streamline employee onboarding by automatically processing HR documents. Extracts employee data, identifies missing fields and compliance issues, logs everything to a tracking sheet, and alerts your HR team via Slack. Perfect for maintaining compliance and ensuring complete onboarding packets.

#### Who is this for?
- HR departments managing employee onboarding
- Onboarding coordinators tracking document completion
- Compliance teams ensuring regulatory requirements
- People operations teams at growing companies

#### How it works
1. **Google Drive Trigger** watches designated folder for new onboarding documents (I-9, W-4, offer letters, etc.)
2. **Download Document** retrieves the HR document from Google Drive
3. **PDF Vector - Extract HR Data** uses AI to extract:
   - Document type (Offer Letter, I-9, W-4, Direct Deposit, Emergency Contact, Policy Acknowledgment, Benefits Enrollment, NDA)
   - Employee information (name, ID, email, phone, address, DOB)
   - Employment details (start date, department, position, manager, salary, pay frequency)
   - Tax withholding information (filing status, allowances)
   - Direct deposit details (bank name, account type - no sensitive account numbers)
   - Emergency contacts (name, relationship, phone)
   - Signatures and dates
4. **Process Document** performs compliance checks:
   - Validates completeness and identifies missing fields
   - Checks for required signatures
   - Formats emergency contacts for tracking
   - Assigns document status (Complete, Incomplete, Needs Review)
   - Flags I-9 forms requiring immediate attention
5. **Log to Onboarding Tracker** appends all data to Google Sheets with:
   - Employee details and contact information
   - Document type and status
   - Issues found and missing fields
   - Emergency contact information
   - Direct link to source document
6. **Notify HR Team** sends Slack alert with:
   - Employee name and department
   - Document type and processing status
   - Visual status indicator (✅ Complete / ⚠️ Needs attention)
   - List of any compliance issues
   - Link to view original document

#### Services used
- Google Drive (document monitoring & storage)
- PDF Vector (AI extraction)
- Google Sheets (onboarding tracker)
- Slack (HR team notifications)

#### Document types supported
- Offer Letters
- I-9 Employment Eligibility Verification
- W-4 Tax Withholding Forms
- Direct Deposit Authorization
- Emergency Contact Forms
- Policy Acknowledgments
- Benefits Enrollment Forms
- Non-Disclosure Agreements (NDAs)
- Other onboarding documents

#### Compliance checks performed
- **Missing signatures**: Flags documents without required signatures
- **Incomplete fields**: Identifies missing required information
- **I-9 status tracking**: Special handling for I-9 forms with completion verification
- **Emergency contacts**: Ensures emergency contact information is provided
- **Document completeness**: Overall assessment of document status

#### Google Sheets structure
| Employee Name | Employee ID | Email | Document Type | Department | Position | Start Date | Status | Issues | Emergency Contacts | Document Link | Processed Date |
|---------------|-------------|-------|---------------|------------|----------|------------|--------|--------|-------------------|---------------|----------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Onboarding Documents" folder in Google Drive
3. Configure Google Drive credentials and set the folder ID in the trigger node
4. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
5. Create a Google Sheet with the columns listed above
6. Configure Google Sheets credentials and set the spreadsheet ID
7. Set up Slack OAuth credentials and select your HR notifications channel
8. Activate the workflow

#### Key features
- Automatic extraction of sensitive data with privacy controls (no account numbers stored)
- Multi-document type support for complete onboarding packets
- I-9 compliance tracking with special status flags
- Missing field identification for follow-up
- Emergency contact formatting and tracking
- Real-time Slack notifications for HR team
- Complete audit trail with document links
- Status tracking (Complete, Incomplete, Needs Review)

#### Real-world use cases
- New employee onboarding packet processing
- I-9 compliance verification and tracking
- Benefits enrollment document management
- Emergency contact information collection
- Policy acknowledgment tracking
- W-4 and direct deposit setup automation

#### Customizing this workflow
- Add additional document types to the extraction schema
- Modify compliance checks for your organization's requirements
- Add email notifications to employees for missing documents
- Connect to your HRIS system instead of Google Sheets
- Add approval workflows for compensation-related documents
- Include document retention rules and expiration tracking
- Set up automated reminders for incomplete documents

</details>

<details>
<summary><strong>🚚 Bill of Lading Tracker</strong> - Track shipments and notify customers | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/bill-of-lading-tracker.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/bill-of-lading-tracker.json">📋 Open</a></summary>

Automatically extract Bill of Lading data from email attachments, log to tracking database, and send professional HTML notification emails to customers.

#### Who is this for?
- Logistics and freight companies
- Shipping departments
- Supply chain managers
- E-commerce businesses tracking shipments

#### How it works
1. **Gmail Trigger** watches for emails with PDF attachments
2. **Get Message** downloads email with all attachments
3. **Split Attachments** processes each BOL separately (handles multiple BOLs per email)
4. **PDF Vector Extract** extracts tracking number, carrier info, shipper/consignee details, origin/destination, items with weights, ship date, and expected delivery
5. **Log to Shipment Tracker** appends shipment data to Google Sheets with "In Transit" status
6. **Send Tracking to Customer** sends professional HTML email with:
   - Highlighted tracking number
   - Complete shipment details table
   - Origin and destination
   - Expected delivery date
   - Confirmation of database logging

#### Services used
- Gmail (email monitoring & sending)
- PDF Vector (AI extraction)
- Google Sheets (shipment tracking)

#### Extracted data fields
- Tracking Number
- Carrier Name & Contact
- Shipper Name & Address
- Consignee Name, Address & Phone
- Origin & Destination
- Line Items (description, quantity, weight)
- Total Weight
- Ship Date
- Expected Delivery

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials
3. Create Google Sheet with columns: Tracking Number, Carrier, Shipper, Consignee, Origin, Destination, Total Weight, Ship Date, Expected Delivery, Status
4. Update the customer notification email address in the Gmail send node
5. Activate the workflow

#### Customizing this workflow
- Add carrier API integration for real-time tracking updates
- Include SMS notifications via Twilio
- Add delivery confirmation workflows
- Connect to your TMS (Transportation Management System)
- Create customer-facing tracking portal

</details>

<details>
<summary><strong>🚢 Shipping Document & Bill of Lading Processor</strong> - Process shipping docs with ETA tracking and alerts | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/shipping-document-processor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/shipping-document-processor.json">📋 Open</a></summary>

Comprehensive shipping document processor that extracts data from Bills of Lading, packing lists, commercial invoices, and customs documents. Features ETA monitoring with urgent arrival alerts and multi-carrier support.

#### Who is this for?
- Logistics and freight forwarding companies
- Import/export businesses
- Supply chain managers
- Shipping departments tracking multiple carriers

#### How it works
1. **Gmail Trigger** monitors inbox for emails with shipping document attachments every minute
2. **Get a message** downloads the email with PDF attachment
3. **PDF Vector - Extract Shipping** uses AI to extract comprehensive shipping data:
   - Document type (Bill of Lading, Packing List, Commercial Invoice, etc.)
   - B/L number and booking reference
   - Shipper and consignee details with addresses
   - Container numbers, types, and seal numbers
   - Vessel name and voyage number
   - Ports of loading and discharge
   - ETD/ETA dates
   - Cargo descriptions with HS codes
   - Weight, volume, and package counts
   - Freight terms and Incoterms
4. **Process Shipping Data** enriches extracted data:
   - Generates shipment ID from B/L or booking number
   - Calculates days to arrival from ETA
   - Determines ETA status (Arrived/Overdue, Arriving Soon, In Transit)
   - Formats container and cargo lists
   - Creates route summary (Port A → Port B)
5. **Log to Shipment Tracker** appends all data to Google Sheets
6. **Arriving Soon?** checks if shipment arrives within 3 days
7. **Urgent - Arriving Soon** (if ≤3 days) sends urgent Slack alert
8. **Notify Logistics Team** (standard path) sends normal notification

#### Services used
- Gmail (email monitoring)
- PDF Vector (AI extraction)
- Google Sheets (shipment tracking)
- Slack (notifications & urgent alerts)

#### Document types supported
- Bills of Lading (B/L)
- Packing Lists
- Commercial Invoices
- Customs Declarations
- Shipping Manifests
- Arrival Notices
- Delivery Orders

#### ETA status indicators
| Status | Days to Arrival | Alert Level |
|--------|-----------------|-------------|
| Arrived/Overdue | ≤ 0 days | 🔴 |
| Arriving Soon | 1-3 days | 🟠 Urgent alert |
| In Transit | > 3 days | 🟢 Normal |

#### Data fields extracted
| Category | Fields |
|----------|--------|
| Document | Type, B/L number, booking number |
| Parties | Shipper name/address/country, consignee name/address/country, notify party |
| Containers | Container numbers, types (20GP, 40GP, 40HC), seal numbers |
| Voyage | Vessel, voyage number, port of loading, port of discharge, place of delivery |
| Dates | ETD, ETA, days to arrival |
| Cargo | Description, HS codes, packages, gross weight, volume/CBM |
| Terms | Freight terms (Prepaid/Collect), Incoterms (FOB, CIF, EXW, etc.) |

#### Google Sheets structure
| Shipment ID | Document Type | B/L Number | Shipper | Consignee | Route | Vessel | ETD | ETA | Days to Arrival | Containers | Container Count | Total Weight (kg) | HS Codes | Incoterms | Received Date |
|-------------|---------------|------------|---------|-----------|-------|--------|-----|-----|-----------------|------------|-----------------|-------------------|----------|-----------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Configure Gmail OAuth credentials for your shipping documents inbox
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and set the spreadsheet ID
6. Set up Slack OAuth credentials and select your logistics channel
7. Activate the workflow

#### Key features
- Multi-document type support (B/L, packing lists, invoices, customs docs)
- Automatic shipment ID generation from B/L or booking number
- ETA monitoring with days-to-arrival calculation
- Urgent alerts for shipments arriving within 3 days
- Container tracking with type identification
- HS code extraction for customs compliance
- Incoterms recognition

#### Customizing this workflow
- Adjust the "Arriving Soon" threshold (currently 3 days) in the IF node
- Add carrier API integration for real-time tracking updates
- Connect to your TMS (Transportation Management System)
- Add SMS notifications for critical shipments via Twilio
- Create customer-facing tracking portal with shipment status
- Add customs clearance status tracking
- Include freight rate validation against quotes

</details>

<details>
<summary><strong>🎓 Research Paper Analyzer & Literature Review</strong> - Extract metadata, find related papers, build citation database | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/research-paper-analyzer.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/research-paper-analyzer.json">📋 Open</a></summary>

Automatically analyze research papers with AI-powered extraction of metadata, findings, and conclusions. Searches academic databases for related papers and builds a comprehensive literature database with auto-generated citations.

#### Who is this for?
- PhD students conducting literature reviews
- Researchers tracking papers in their field
- Academic writers managing references
- Anyone building a knowledge base from research papers

#### How it works
1. **Google Drive Trigger** monitors your research papers folder for new PDF uploads
2. **Download Paper** retrieves the PDF from Google Drive
3. **PDF Vector - Extract Paper Info** uses AI to extract comprehensive metadata:
   - Title, authors, journal, publication year, DOI
   - Full abstract and keywords
   - Research field and study type (Experimental, Review, Meta-analysis, etc.)
   - Sample size, methodology summary
   - Main findings, conclusions, limitations
   - Future research suggestions
4. **PDF Vector - Find Related Papers** searches Semantic Scholar and PubMed using paper keywords
5. **Compile Analysis** formats all data:
   - Generates APA-style citation
   - Creates author list and keyword summary
   - Formats related papers with citation counts
   - Prepares Notion summary content
6. **Add to Literature Database** logs comprehensive paper data to Google Sheets
7. **Create Notion Summary** creates a new page with paper summary for easy reference

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction & academic search)
- Google Sheets (literature database)
- Notion (paper summaries)

#### Study types detected
- Experimental
- Observational
- Review
- Meta-analysis
- Case Study
- Qualitative
- Mixed Methods
- Theoretical

#### Academic databases searched
- Semantic Scholar
- PubMed

#### Google Sheets structure
| Title | Authors | Year | Journal | DOI | Research Field | Study Type | Sample Size | Keywords | Abstract | Conclusions | Citation | Related Papers Found | File Link | Added Date |
|-------|---------|------|---------|-----|----------------|------------|-------------|----------|----------|-------------|----------|---------------------|-----------|------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Research Papers" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Create a parent page in Notion for paper summaries
7. Configure Notion credentials and set the parent page ID
8. Activate the workflow

#### Key features
- Comprehensive metadata extraction (15+ fields)
- Automatic study type classification
- Related paper discovery across multiple databases
- APA-style citation generation
- Notion integration for quick paper summaries
- Direct links to original papers in Google Drive

#### Customizing this workflow
- Add more academic databases (arXiv, Google Scholar via custom nodes)
- Create citation network visualizations
- Add Slack notifications for high-impact related papers
- Integrate with reference managers (Zotero, Mendeley)
- Add duplicate paper detection
- Create weekly literature digest reports
- Tag papers by research theme or project

</details>

<details>
<summary><strong>🏠 Lease Agreement Analyzer for Renters</strong> - Analyze leases, extract terms, and detect red flags | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/lease-agreement-analyzer.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/lease-agreement-analyzer.json">📋 Open</a></summary>

Automatically analyze residential lease agreements with AI-powered extraction of key terms, financial details, and red flag detection. Perfect for renters who want to understand their lease before signing and identify potentially unfair clauses.

#### Who is this for?
- Renters reviewing leases before signing
- Property managers evaluating lease templates
- Real estate agents assisting clients
- Tenant advocates helping renters understand their rights

#### How it works
1. **Google Drive Trigger** monitors your lease documents folder for new PDF uploads
2. **Download Lease** retrieves the PDF from Google Drive
3. **PDF Vector - Analyze Lease** uses AI to extract comprehensive lease data:
   - Property address and unit information
   - Landlord and tenant details
   - Monthly rent and security deposit amounts
   - Lease duration, start/end dates, renewal terms
   - Pet policy (allowed, deposits, restrictions)
   - Included utilities and parking
   - Late payment fees and grace periods
   - Early termination penalties
   - Maintenance responsibilities (landlord vs tenant)
   - Red flags with severity levels (High/Medium/Low)
4. **Merge Data** combines extracted data with original file
5. **PDF Vector - Tenant Advice** generates tenant advocacy analysis:
   - Overall lease summary
   - Top 3 negotiation points
   - Fairness rating (Tenant-Friendly, Neutral, Landlord-Friendly)
   - Warnings about problematic terms
6. **Compile Analysis** processes all data:
   - Calculates total move-in cost (rent + deposits)
   - Formats landlord and tenant information
   - Summarizes red flags and determines overall risk level
   - Truncates advice for spreadsheet compatibility
7. **Log Lease Analysis** appends comprehensive data to Google Sheets
8. **High Risk?** checks if lease has High risk level
9. **High Risk Alert** (if high risk) sends urgent Slack notification with red flags
10. **Analysis Complete** (standard path) sends Slack confirmation with lease summary

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction & analysis)
- Google Sheets (lease tracking database)
- Slack (notifications & alerts)

#### Red flags detected
- Excessive fees or penalties
- Unreasonable termination clauses
- Missing standard tenant protections
- Vague or ambiguous language
- One-sided maintenance responsibilities
- Unusual security deposit requirements
- Problematic auto-renewal terms

#### Risk level calculation
- **High** - 2 or more high-severity red flags
- **Medium** - 1 high-severity flag OR 3+ total flags
- **Low** - Minor issues or no red flags identified

#### Google Sheets structure
| Property Address | Landlord | Tenants | Monthly Rent | Security Deposit | Move-In Cost | Lease Start | Lease End | Pet Policy | Utilities Included | Late Fee | Early Termination | Red Flags | Risk Level | Tenant Advice | Analyzed Date |
|------------------|----------|---------|--------------|------------------|--------------|-------------|-----------|------------|-------------------|----------|-------------------|-----------|------------|---------------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Lease Documents" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack OAuth credentials and select your notification channel
7. Activate the workflow

#### Key features
- Comprehensive lease term extraction (20+ fields)
- AI-powered red flag detection with severity levels
- Tenant advocacy analysis with negotiation tips
- Total move-in cost calculation
- Risk-based Slack alerting
- Fairness rating for quick assessment

#### Customizing this workflow
- Adjust red flag detection criteria in the extraction prompt
- Modify risk level thresholds in the "Compile Analysis" node
- Add email notifications alongside Slack alerts
- Connect to a tenant rights database for jurisdiction-specific advice
- Add comparison against standard lease templates
- Include rent-to-income ratio calculations
- Create renewal reminder workflows based on lease end dates

</details>

<details>
<summary><strong>📝 Meeting Notes & Action Item Extractor</strong> - Extract action items and decisions from meeting notes | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/meeting-notes-extractor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/meeting-notes-extractor.json">📋 Open</a></summary>

Automatically process meeting notes and transcripts with AI-powered extraction of attendees, discussion points, decisions, and action items. Logs comprehensive summaries to Google Sheets and posts formatted updates to Slack with task assignments and due dates.

#### Who is this for?
- Project managers tracking action items across multiple meetings
- Team leads distributing meeting summaries to stakeholders
- Executive assistants organizing follow-ups and next steps
- Scrum masters documenting sprint planning and retrospectives

#### How it works
1. **Google Drive Trigger** monitors your meeting notes folder for new documents
2. **Download Notes** retrieves the PDF or document from Google Drive
3. **PDF Vector - Extract Meeting Info** uses AI to extract comprehensive meeting data:
   - Meeting title, date, and duration
   - Attendees with names, roles, and emails
   - Agenda items discussed
   - Key discussion points with topic summaries
   - Decisions made with rationale and decision makers
   - Action items with task descriptions, assigned owners, due dates, and priority levels (High/Medium/Low)
   - Follow-up meeting details (date and purpose)
   - Parking lot items for future discussion
4. **Format Meeting Data** processes extracted data:
   - Creates formatted attendee list
   - Counts total attendees
   - Formats discussion points with bullet points
   - Formats decisions with checkmarks
   - Formats action items with task owners and due dates
   - Counts total decisions and action items
   - Identifies high-priority action items
5. **Log Meeting Summary** appends summary to Google Sheets with:
   - Meeting title, date, duration
   - Attendee list and count
   - Number of decisions made
   - Number of action items
   - High-priority action item count
   - Follow-up meeting date
   - Direct link to meeting notes
   - Processing timestamp
6. **Post Summary to Slack** sends formatted message with:
   - Meeting title and date
   - Attendee list
   - All decisions made with counts
   - All action items with owners, due dates, and priorities
   - Next meeting information (if scheduled)
   - Link to full notes in Google Drive

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction)
- Google Sheets (meeting summary tracking)
- Slack (team notifications)

#### Extracted fields
| Category | Fields |
|----------|--------|
| Meeting Info | Title, date, duration |
| Attendees | Name, role, email |
| Discussion | Agenda items, key discussion points with topics and summaries |
| Decisions | Decision text, rationale, decision maker |
| Action Items | Task description, assigned owner, due date, priority (High/Medium/Low) |
| Follow-up | Next meeting date and purpose |
| Parking Lot | Items deferred for future discussion |

#### Google Sheets structure
| Meeting Title | Date | Duration | Attendees | Attendee Count | Decisions Made | Action Items | High Priority | Follow-up Date | Notes Link | Processed |
|---------------|------|----------|-----------|----------------|----------------|--------------|---------------|----------------|------------|-----------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Meeting Notes" folder in Google Drive and configure the trigger with the folder ID
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the columns listed above
5. Configure Google Sheets credentials and spreadsheet ID
6. Set up Slack OAuth credentials and select your team notification channel
7. Activate the workflow

#### Key features
- Comprehensive meeting data extraction (9 categories)
- Automatic action item prioritization (High/Medium/Low)
- Owner assignment tracking for accountability
- Due date extraction for deadline management
- Decision documentation with rationale
- Follow-up meeting scheduling
- Direct links to original meeting notes
- Formatted Slack notifications with task assignments

#### Customizing this workflow
- Add email notifications to action item owners
- Create calendar events for action item due dates
- Integrate with project management tools (Asana, Jira, Monday.com)
- Add reminders for overdue action items
- Filter high-priority items to separate Slack channel
- Connect to your team wiki or knowledge base
- Add participant attendance tracking
- Create weekly action item digest reports

</details>

<details>
<summary><strong>🎓 Academic Paper Finder & Citation Generator</strong> - Search academic databases and generate citations | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/academic-paper-finder.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/academic-paper-finder.json">📋 Open</a></summary>

Automatically search Semantic Scholar, PubMed, and ArXiv for academic papers based on research queries. Ranks results by citation count, retrieves the top 10 most-cited papers, and generates both APA and BibTeX citations ready for use in your manuscripts.

#### Who is this for?
- PhD students conducting comprehensive literature reviews
- Researchers exploring new research areas and finding related work
- Academic writers needing properly formatted citations quickly
- Literature review authors tracking citation metrics for papers

#### How it works
1. **Every Minute** checks for new research queries to process
2. **Read Queries** fetches rows from Google Sheets where Status = "Pending"
3. **Status = Pending?** filters for rows with valid search queries and Pending status
4. **PDF Vector - Search Papers** searches three academic databases simultaneously:
   - Semantic Scholar (comprehensive multi-disciplinary coverage)
   - PubMed (medical and life sciences papers)
   - ArXiv (physics, mathematics, computer science preprints)
5. **Process & Format Results** analyzes up to 20 results and:
   - Sorts all papers by citation count (most influential papers first)
   - Selects top 10 most-cited papers
   - Generates APA format citations with authors, year, title, venue, and DOI
   - Generates BibTeX entries with auto-generated citation keys
   - Creates paper list with titles, years, and citation counts
   - Calculates total citations across all top papers
   - Identifies the most cited paper as the key reference
6. **Update Results** writes comprehensive data back to Google Sheets:
   - Top papers list with citation counts
   - Total results found across all databases
   - APA formatted citations (copy-paste ready)
   - BibTeX entries (ready for LaTeX documents)
   - Most cited paper highlight
   - Search date for tracking when results were retrieved
   - Status changed to "Completed"

#### Services used
- Google Sheets (query management & results storage)
- PDF Vector (academic database search with Semantic Scholar, PubMed, ArXiv)
- Schedule Trigger (automated processing)

#### Google Sheets structure
| Search Query | Status | Results Found | Top Papers | Total Citations | Most Cited | APA Citations | BibTeX Citations | Search Date |
|--------------|--------|---------------|------------|-----------------|------------|---------------|------------------|-------------|

**Required columns:**
- **Search Query** (Column A): Your research query (e.g., "machine learning in healthcare")
- **Status** (Column B): Set to "Pending" to trigger search, automatically becomes "Completed" when done

**Auto-populated columns:**
- **Results Found**: Total number of papers found across all three databases
- **Top Papers**: List of top 10 papers with titles, years, and citation counts
- **Total Citations**: Sum of all citations for the top 10 papers
- **Most Cited**: The highest-impact paper from your search results
- **APA Citations**: Ready-to-use APA format citations for all top 10 papers
- **BibTeX Citations**: LaTeX-ready BibTeX entries for bibliography files
- **Search Date**: When the search was performed (useful for tracking result freshness)

#### Setup instructions
1. Import the workflow into n8n
2. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
3. Create a Google Sheet with the columns listed above (9 columns total)
4. Configure Google Sheets OAuth credentials in both "Read Queries" and "Update Results" nodes
5. Update the spreadsheet ID in both Google Sheets nodes
6. Activate the workflow (it will check for pending queries every minute)

#### Key features
- Multi-database search across Semantic Scholar, PubMed, and ArXiv in one query
- Automatic ranking by citation count to surface the most influential papers
- Dual citation format generation (APA and BibTeX) for different writing workflows
- Citation metrics tracking (total citations, most cited paper)
- Status-based processing (only searches "Pending" rows)
- Re-searchable queries (change Status back to "Pending" to refresh results)
- Automated processing every minute for hands-free operation
- Comprehensive paper metadata (authors, year, venue, DOI)

#### Real-world use case
A PhD student researching "neural networks for medical image segmentation" adds this query to their Google Sheet with Status="Pending". Within a minute, the workflow:
- Finds 47 papers across Semantic Scholar, PubMed, and ArXiv
- Returns top 10 most-cited papers (ranging from 89 to 2,847 citations)
- Generates 10 APA citations ready to paste into their dissertation
- Creates 10 BibTeX entries for their LaTeX bibliography
- Shows the most cited paper is "U-Net: Convolutional Networks..." with 2,847 citations
- Total 8,234 citations across top papers, validating this is a well-established research area

#### Customizing this workflow
- Adjust search frequency by changing the Schedule Trigger interval (currently every minute)
- Increase the limit parameter in "PDF Vector - Search Papers" to get more than 20 initial results
- Modify the top papers count in the Code node (currently top 10, can increase to 15 or 20)
- Add additional citation formats (MLA, Chicago) in the formatting logic
- Filter by publication year to focus on recent papers only
- Add email notifications when searches complete for important queries
- Create separate sheets for different research topics
- Add abstract summaries to the results for quick paper evaluation
- Include journal impact factors alongside citation counts
- Add links to full-text PDFs when available from the databases

</details>

<details>
<summary><strong>📊 Competitor Analysis from Reports & Documents</strong> - Extract intelligence from competitor docs with strategic insights | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/competitor-analysis-extractor.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/competitor-analysis-extractor.json">📋 Open</a></summary>

Automatically monitor competitor documents (annual reports, earnings calls, SEC filings, press releases) and extract competitive intelligence with AI-powered strategic analysis. Captures financials, products, initiatives, partnerships, and generates actionable business insights for your strategy team.

#### Who is this for?
- Market research teams tracking competitor moves and market positioning
- Business analysts building competitive intelligence databases
- Product managers monitoring competitor product launches and features
- Strategic planners identifying market threats and opportunities
- Venture capital firms analyzing portfolio companies and competitors

#### How it works
1. **Google Drive Trigger** monitors your designated "Competitor Documents" folder for new files
2. **Download Document** retrieves the PDF from Google Drive
3. **PDF Vector - Extract Intel** uses AI to extract structured competitive intelligence:
   - Company name and document type (Annual Report, Earnings Call, Press Release, SEC Filing, etc.)
   - Report period for temporal tracking
   - Financial metrics: revenue, revenue growth rate, net income, market share, employee count
   - Product announcements with names, descriptions, and status (New/Updated/Existing/Discontinued)
   - Strategic initiatives with priority levels and timelines
   - Partnerships, acquisitions, and market expansion plans
   - Technology investments and R&D focus areas
   - Identified threats to their business
   - Opportunities they're pursuing
   - Key quotes from executives for context
4. **Merge Data** combines extracted intelligence with document metadata
5. **PDF Vector - Strategic Insights** generates AI-powered strategic analysis:
   - 2-3 sentence executive summary of competitor's current market position
   - Top 3 strategic moves to watch closely
   - Impact assessment on your business
   - Recommended actions for your team
6. **Compile Intelligence** processes and formats all data:
   - Creates financial summary string for easy reading
   - Lists new product launches
   - Formats strategic initiatives as bullet points
   - Counts threats and opportunities
   - Combines structured data with strategic insights
7. **Log to Intel Database** appends comprehensive data to Google Sheets:
   - Competitor name, document type, report period
   - Financial summary (revenue, growth, market share)
   - New products, partnerships, acquisitions
   - Threat and opportunity counts
   - Direct link to source document
   - Analysis date for tracking intelligence freshness
8. **Share with Strategy Team** posts detailed Slack alert with:
   - Company and document overview
   - Financial highlights
   - New product announcements
   - Strategic initiatives list
   - Threat/opportunity counts
   - AI-generated strategic analysis and recommendations
   - Link to full source document

#### Services used
- Google Drive (file monitoring & download)
- PDF Vector (AI extraction & strategic analysis)
- Google Sheets (intelligence database)
- Slack (team notifications)

#### Extracted fields
| Category | Fields |
|----------|--------|
| Company Info | Company name, document type, report period |
| Financials | Revenue, revenue growth %, net income, market share %, employees |
| Products | Product name, description, status (New/Updated/Existing/Discontinued) |
| Strategy | Initiatives with priority and timeline |
| Partnerships | Partnership announcements |
| M&A | Acquisition targets and completed deals |
| Expansion | Market expansion plans and regions |
| Technology | Technology investments and R&D focus |
| Analysis | Threats identified, opportunities spotted, key executive quotes |

#### Google Sheets structure
| Competitor | Document Type | Report Period | Financials | New Products | Partnerships | Acquisitions | Threats Identified | Opportunities | Source Document | Analysis Date |
|------------|---------------|---------------|------------|--------------|--------------|--------------|-------------------|---------------|-----------------|---------------|

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Competitor Documents" folder in Google Drive for dropping annual reports, earnings transcripts, etc.
3. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
4. Create a Google Sheet with the 11 columns listed above
5. Configure Google Drive OAuth credentials and set the folder ID in the trigger
6. Configure Google Sheets OAuth credentials and set your spreadsheet ID
7. Set up Slack OAuth credentials and select your #strategy-team or #competitor-intel channel
8. Activate the workflow

#### Key features
- Comprehensive competitive intelligence extraction (11 data categories)
- AI-generated strategic analysis with business impact assessment
- Recommended actions for your team based on competitor moves
- Financial metrics tracking over time
- Product launch monitoring
- M&A activity tracking
- Market expansion identification
- Threat and opportunity scoring
- Direct links to source documents for reference
- Real-time Slack alerts to keep strategy team informed

#### Real-world use case
A product manager at a SaaS company drops a competitor's Q4 earnings call transcript into Google Drive. Within minutes, the workflow:
- Extracts that the competitor has $180M revenue with 65% YoY growth
- Identifies 3 new product features they're launching (AI assistant, mobile app, SSO)
- Captures their partnership with Microsoft and acquisition of a smaller analytics startup
- Detects 2 threats they mentioned (increasing customer acquisition costs, macroeconomic headwinds)
- Spots 3 opportunities (enterprise market expansion, international growth, usage-based pricing)
- Generates AI analysis: "Competitor is aggressively expanding upmarket with enterprise features while maintaining SMB base. Watch their AI assistant launch closely as it directly competes with our roadmap. Recommend accelerating our own AI feature development and emphasizing our superior pricing model."
- Logs everything to Google Sheets for quarterly competitive analysis reports
- Posts detailed summary to #strategy-team Slack channel for immediate visibility

#### Customizing this workflow
- Add email notifications to specific stakeholders for high-priority threats
- Create separate Google Sheets tabs for different competitors
- Add sentiment analysis of executive tone in earnings calls
- Connect to your CRM to correlate competitor moves with your win/loss data
- Build trend dashboards in Google Sheets using the logged data
- Add automatic follow-up tasks in Asana/Jira when specific keywords are detected
- Filter alerts by competitor priority (Tier 1 vs Tier 2 competitors)
- Add comparison against your own company metrics
- Create monthly competitive intelligence summary reports
- Set up keyword alerts for specific technologies or market segments

</details>

<details>
<summary><strong>🛡️ Warranty Document & Claim Tracker</strong> - Track product warranties and get expiration alerts | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/warranty-document-tracker.json">⬇️ Download</a> | <a href="https://github.com/khanhduyvt0101/workflows/blob/main/n8n-workflows/warranty-document-tracker.json">📋 Open</a></summary>

Never miss a warranty expiration again! Automatically extract warranty information from product documentation, track coverage periods, calculate expiration dates, and receive Slack alerts when warranties are expiring soon. Perfect for consumers, customer service teams, and businesses managing product inventories.

#### Who is this for?
- Consumers tracking warranties on personal electronics, appliances, and purchases
- Customer service teams managing product warranty claims
- Retail businesses tracking inventory warranties
- Electronics companies managing warranty coverage
- IT departments tracking equipment warranties

#### How it works
1. **Google Drive Trigger** watches designated folder for new warranty documents (receipts, warranty cards, product manuals)
2. **Download Document** retrieves the warranty PDF from Google Drive
3. **PDF Vector - Extract Warranty** uses AI to extract comprehensive warranty data:
   - Product information (name, brand, model, serial number, category)
   - Purchase details (date, retailer, price, receipt number)
   - Warranty terms (type, duration in months, start date, end date)
   - Coverage details (what's covered, exclusions)
   - Claim process and contact information
4. **Process Warranty** calculates warranty status:
   - Computes warranty end date if not explicitly stated (purchase date + duration)
   - Calculates days remaining until expiration
   - Assigns status: "Active", "Active - Expires in 3 months", "Expiring Soon" (≤30 days), or "Expired"
   - Formats coverage and exclusions lists for easy reference
5. **Log to Warranty Tracker** appends complete warranty record to Google Sheets with:
   - Product details and serial number
   - Purchase information and retailer
   - Warranty type and expiration date
   - Days remaining and current status
   - Coverage summary
   - Direct link to warranty document
6. **Expiring Soon?** checks if warranty is expiring within 30 days
7. **Alert Expiring** (if expiring soon) sends Slack notification with:
   - Product name, brand, and model
   - Expiration date and days remaining
   - Coverage summary
   - Reminder to file claims before expiration

#### Services used
- Google Drive (document monitoring & storage)
- PDF Vector (AI extraction)
- Google Sheets (warranty tracker database)
- Slack (expiration alerts)

#### Warranty types supported
- Limited warranties
- Full warranties
- Extended warranties
- Lifetime warranties
- Manufacturer warranties

#### Extracted data fields
- **Product**: Name, brand, model, serial number, category
- **Purchase**: Date, retailer, price, receipt number
- **Warranty**: Type, duration, start date, end date
- **Coverage**: What's covered (parts, labor, defects)
- **Exclusions**: What's not covered (misuse, water damage, etc.)
- **Claims**: Claim process steps and contact information (phone, email, website, address)

#### Google Sheets structure
| Product | Brand | Model | Serial Number | Purchase Date | Purchase Price | Retailer | Warranty Type | Expires | Days Remaining | Status | Coverage | Document Link | Added Date |
|---------|-------|-------|---------------|---------------|----------------|----------|---------------|---------|----------------|--------|----------|---------------|------------|

#### Status categories
- **Active**: More than 90 days remaining
- **Active - Expires in 3 months**: 31-90 days remaining
- **Expiring Soon**: 30 days or less remaining (triggers Slack alert)
- **Expired**: Warranty period has ended
- **Unknown**: Unable to determine expiration date

#### Setup instructions
1. Import the workflow into n8n
2. Create a "Warranty Documents" folder in Google Drive
3. Configure Google Drive credentials and set the folder ID in the trigger node
4. Get your PDF Vector API key from [pdfvector.com/api-keys](https://pdfvector.com/api-keys)
5. Create a Google Sheet with the columns listed above
6. Configure Google Sheets credentials and set the spreadsheet ID
7. Set up Slack OAuth credentials and select your notifications channel (e.g., #warranty-alerts)
8. Activate the workflow

#### Key features
- Automatic warranty expiration calculation
- Smart status detection (Active, Expiring Soon, Expired)
- 30-day advance warning alerts via Slack
- Complete coverage and exclusions tracking
- Serial number logging for claim filing
- Direct links to warranty documents
- Purchase history tracking with receipts
- Multi-warranty type support

#### Real-world use cases
- **Consumer**: Track warranties on all home electronics, appliances, and major purchases. Get reminded 30 days before warranty expires so you can file claims for any issues.
- **Customer Service**: Maintain a database of product warranties to quickly verify coverage when customers call. Know exactly what's covered and how to file claims.
- **Retail Store**: Track warranties on inventory and demo units. Know which products are still under manufacturer warranty for returns or repairs.
- **IT Department**: Manage warranties on laptops, monitors, servers, and network equipment. Plan equipment replacements based on warranty expiration.
- **Electronics Repair Shop**: Keep records of customer product warranties to advise on coverage before starting repairs.

#### Customizing this workflow
- Adjust the "Expiring Soon" threshold (currently 30 days) to match your preferences
- Add email notifications alongside Slack alerts
- Create separate Slack channels for different product categories
- Add calendar events for warranty expirations
- Set up automated reminders at multiple intervals (90 days, 60 days, 30 days)
- Connect to asset management systems instead of Google Sheets
- Add QR code generation for quick warranty lookup
- Include warranty renewal tracking for extended warranties
- Add cost-benefit analysis for extended warranty purchases
- Create reports on warranty utilization and claim frequency

</details>

### How to Import

#### Option 1: Copy & Paste (Recommended)
1. **Click** the **Download** link next to any workflow
2. The JSON will open in your browser - press `Ctrl+A` (Windows/Linux) or `Cmd+A` (Mac) to **select all**
3. Press `Ctrl+C` (Windows/Linux) or `Cmd+C` (Mac) to **copy** the content
4. In n8n, open the **Workflows** panel
5. Press `Ctrl+V` (Windows/Linux) or `Cmd+V` (Mac) to **paste** - n8n will automatically create the workflow!

> This is the fastest method - just click, select all, copy, and paste directly into n8n!

#### Option 2: Direct Download
1. **Right-click** the **Download** link next to any workflow
2. Select **"Save Link As..."** (Chrome/Edge) or **"Download Linked File"** (Safari)
3. Save the `.json` file to your computer
4. In n8n, click **Workflows** in the sidebar
5. Click **Add Workflow** → **Import from File**
6. Select your downloaded file

---

## Zapier Workflows

> Coming Soon - Zapier Zaps for PDF automation will be added in future updates.

---

## Make.com Workflows

> Coming Soon - Make.com scenarios for PDF processing will be added in future updates.

---

## Contributing

Contributions are welcome! If you have a PDF automation workflow to share:

1. Fork this repository
2. Add your workflow JSON to the appropriate folder
3. Update the README with your workflow details
4. Submit a pull request

---

## License

MIT License - Feel free to use, modify, and share these workflows.
