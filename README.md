# Awesome PDF Automation Workflows

![n8n Workflows](https://img.shields.io/badge/n8n-11_workflows-FF6D5A)
![Zapier](https://img.shields.io/badge/Zapier-coming_soon-FF4A00)
![Make](https://img.shields.io/badge/Make.com-coming_soon-6E52FF)
![License](https://img.shields.io/badge/License-MIT-green)

> A curated collection of ready-to-use automation workflows for **PDF processing**, **document extraction**, and **intelligent document automation**.

Transform your document workflows with AI-powered automation. Extract data from invoices, process resumes, validate contracts, and more!

---

## Supported Platforms

| Platform | Status | Workflows | Folder |
|:--------:|:------:|:---------:|:------:|
| ![n8n](https://img.shields.io/badge/-n8n-FF6D5A?style=flat&logo=n8n&logoColor=white) | Available | 11 | [`n8n-workflows/`](n8n-workflows/) |
| ![Zapier](https://img.shields.io/badge/-Zapier-FF4A00?style=flat&logo=zapier&logoColor=white) | Coming Soon | - | [`zapier-workflows/`](zapier-workflows/) |
| ![Make](https://img.shields.io/badge/-Make.com-6E52FF?style=flat&logo=make&logoColor=white) | Coming Soon | - | [`make-workflows/`](make-workflows/) |

---

## n8n Workflows

> **About n8n**: These workflows are designed for [n8n](https://n8n.io/) - a fair-code workflow automation platform. You'll need an n8n instance (self-hosted or cloud) to use these workflows.

### Requirements

Before importing, ensure you have:
- An **n8n instance** (self-hosted or [n8n Cloud](https://n8n.io/cloud/))
- The **[PDF Vector](https://www.npmjs.com/package/n8n-nodes-pdfvector)** community node installed (required for document AI features)
- Relevant **credentials** configured (Google, Slack, etc.)

### Quick Start

1. Click the **Download** link for the workflow you want
2. Open your n8n instance
3. Go to **Workflows** → **Import from File**
4. Select the downloaded JSON file
5. Configure your credentials in each node
6. Click **Activate** to start the workflow!

### Available Workflows

| | Workflow | Description | Actions |
|:---:|---|---|:---:|
| 📄 | **Invoice Data Extraction** | Extract structured data from invoice PDFs using AI and save to Google Sheets | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-data-extraction.json) · [View](n8n-workflows/invoice-data-extraction.json) |
| 💰 | **Invoice Processing & Approval** | Process invoices with approval routing, budget validation, and Slack notifications | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/invoice-processing-approval.json) · [View](n8n-workflows/invoice-processing-approval.json) |
| 📧 | **Gmail Invoice Processor** | Monitor Gmail for invoice PDFs and create formatted Google Docs automatically | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/gmail-invoice-processor.json) · [View](n8n-workflows/gmail-invoice-processor.json) |
| 💰 | **Tax Document Organizer** | Categorize and organize tax PDFs from email attachments automatically | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/tax-document-organizer.json) · [View](n8n-workflows/tax-document-organizer.json) |
| 🏥 | **Insurance Pre-Authorization** | Process insurance authorization PDFs with automated document extraction | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/insurance-pre-authorization.json) · [View](n8n-workflows/insurance-pre-authorization.json) |
| 🏥 | **Medical Records Intake** | Automate patient medical records PDF intake and organization | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/medical-records-intake.json) · [View](n8n-workflows/medical-records-intake.json) |
| ⚖️ | **NDA Compliance Checker** | Validate NDA documents for compliance using AI-powered PDF analysis | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/nda-compliance-checker.json) · [View](n8n-workflows/nda-compliance-checker.json) |
| 🏠 | **Mortgage Application Validator** | Validate mortgage application PDFs and extract key information | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/mortgage-application-validator.json) · [View](n8n-workflows/mortgage-application-validator.json) |
| 🎓 | **Education Transcript Processor** | Extract and process academic transcript PDFs for verification | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/education-transcript-processor.json) · [View](n8n-workflows/education-transcript-processor.json) |
| 👤 | **Resume Parser & Scoring** | Parse resume PDFs, score candidates, and log to Google Sheets with Slack alerts | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/resume-parser.json) · [View](n8n-workflows/resume-parser.json) |
| 🚚 | **Bill of Lading Tracker** | Track and process bill of lading documents for logistics management | [Download](https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/bill-of-lading-tracker.json) · [View](n8n-workflows/bill-of-lading-tracker.json) |

### Categories

| Icon | Category | Workflows |
|:---:|---|---|
| 📄 | PDF Extraction | Invoice Data Extraction |
| 💰 | Finance & Invoicing | Invoice Processing, Gmail Invoice Processor, Tax Document Organizer |
| 🏥 | Healthcare Documents | Insurance Pre-Authorization, Medical Records Intake |
| ⚖️ | Legal Documents | NDA Compliance Checker |
| 🏠 | Real Estate Documents | Mortgage Application Validator |
| 🎓 | Education Documents | Education Transcript Processor |
| 👤 | HR Documents | Resume Parser & Scoring |
| 🚚 | Logistics Documents | Bill of Lading Tracker |

### How to Import

#### Option 1: Direct Download
1. Click the **Download** link next to any workflow
2. Save the `.json` file to your computer
3. In n8n, click **Workflows** in the sidebar
4. Click **Add Workflow** → **Import from File**
5. Select your downloaded file

#### Option 2: Import from URL
1. Copy the **Download** link URL
2. In n8n, click **Add Workflow** → **Import from URL**
3. Paste the URL and click **Import**

---

## Zapier Workflows

> Coming Soon - Zapier Zaps for PDF automation will be added in future updates.

---

## Make.com Workflows

> Coming Soon - Make.com scenarios for PDF processing will be added in future updates.

---

## Repository Structure

```
workflows/
├── README.md                  # This file
├── n8n-workflows/             # n8n workflow JSON files
│   ├── invoice-data-extraction.json
│   ├── invoice-processing-approval.json
│   ├── gmail-invoice-processor.json
│   ├── tax-document-organizer.json
│   ├── insurance-pre-authorization.json
│   ├── medical-records-intake.json
│   ├── nda-compliance-checker.json
│   ├── mortgage-application-validator.json
│   ├── education-transcript-processor.json
│   ├── resume-parser.json
│   └── bill-of-lading-tracker.json
├── zapier-workflows/          # Zapier Zap templates (coming soon)
└── make-workflows/            # Make.com scenario files (coming soon)
```

---

## Features

- **AI-Powered Extraction** - Use GPT and vision models to extract data from any PDF
- **Structured Output** - Get clean, structured data ready for your databases
- **Smart Notifications** - Slack, email, and webhook integrations
- **Google Sheets Integration** - Automatic logging and data storage
- **One-Click Import** - Ready-to-use JSON templates

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
