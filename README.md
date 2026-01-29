# Awesome PDF Automation Workflows

![n8n Workflows](https://img.shields.io/badge/n8n-14_workflows-FF6D5A)
![Zapier](https://img.shields.io/badge/Zapier-coming_soon-FF4A00)
![Make](https://img.shields.io/badge/Make.com-coming_soon-6E52FF)
![License](https://img.shields.io/badge/License-MIT-green)

> A curated collection of ready-to-use automation workflows for **PDF processing**, **document extraction**, and **intelligent document automation**.

Transform your document workflows with AI-powered automation. Extract data from invoices, process resumes, validate contracts, and more!

---

## Supported Platforms

| Platform | Status | Workflows | Folder |
|:--------:|:------:|:---------:|:------:|
| ![n8n](https://img.shields.io/badge/-n8n-FF6D5A?style=flat&logo=n8n&logoColor=white) | Available | 14 | [`n8n-workflows/`](n8n-workflows/) |
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
<summary><strong>📄 Invoice Data Extraction</strong> - Extract structured data from invoice PDFs | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-data-extraction.json">⬇️ Download</a></summary>

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
<summary><strong>💰 Invoice Processing & Approval</strong> - Enterprise invoice workflow with fraud detection | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-approval.json">⬇️ Download</a></summary>

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
<summary><strong>📧 Gmail Invoice Processor</strong> - Convert invoice PDFs to formatted Google Docs | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/gmail-invoice-processor.json">⬇️ Download</a></summary>

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
<summary><strong>💰 Invoice Processing - AP Automation</strong> - Automate accounts payable with PO matching | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-ap-automation.json">⬇️ Download</a></summary>

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
<summary><strong>💰 Invoice Processing with Validation</strong> - Extract and validate invoice math automatically | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-validation.json">⬇️ Download</a></summary>

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
<summary><strong>💰 Tax Document Organizer</strong> - Auto-categorize and file tax documents | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/tax-document-organizer.json">⬇️ Download</a></summary>

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
<summary><strong>💳 Expense Report Processor</strong> - Auto-categorize expenses with AI and route for approval | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/expense-report-processor.json">⬇️ Download</a></summary>

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
<summary><strong>🏥 Insurance Pre-Authorization</strong> - Process prior auth requests with emergency fast-tracking | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/insurance-pre-authorization.json">⬇️ Download</a></summary>

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
<summary><strong>🏥 Medical Records Intake</strong> - Automate patient intake form processing | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/medical-records-intake.json">⬇️ Download</a></summary>

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
<summary><strong>⚖️ NDA Compliance Checker</strong> - Validate NDAs for required clauses and risk | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/nda-compliance-checker.json">⬇️ Download</a></summary>

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
<summary><strong>🏠 Mortgage Application Validator</strong> - Validate applications with DTI/LTV calculations | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/mortgage-application-validator.json">⬇️ Download</a></summary>

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
<summary><strong>🎓 Education Transcript Processor</strong> - Process transcripts with GPA analysis | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/education-transcript-processor.json">⬇️ Download</a></summary>

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
<summary><strong>👤 Resume Parser & Scoring</strong> - Parse and score candidates automatically | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/resume-parser.json">⬇️ Download</a></summary>

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
<summary><strong>🚚 Bill of Lading Tracker</strong> - Track shipments and notify customers | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/bill-of-lading-tracker.json">⬇️ Download</a></summary>

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
