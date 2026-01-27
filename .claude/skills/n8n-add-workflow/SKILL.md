---
name: n8n-add-workflow
description: Add a new n8n workflow template to the repository. Use when user provides n8n workflow JSON to add.
user-invocable: true
argument-hint: [workflow-name]
---

# n8n Add Workflow Skill

This skill guides you through adding a new n8n workflow template to this repository.

## When to Use

Use this skill when:
- User provides n8n workflow JSON content to add
- User wants to add a new workflow template to the collection
- User shares a workflow they want documented and saved

## Required Input

- **Workflow JSON** (required) - The n8n workflow JSON content from the user
- **Name** (optional) - Can be extracted from JSON `name` field
- **Description** (optional) - Can be generated from workflow analysis

## Step-by-Step Process

### 1. Parse the Workflow JSON

Extract key information from the JSON:
- `name` field for the workflow name
- `nodes` array to identify all node types and services used
- Look for trigger nodes to understand how the workflow starts

### 2. Generate the Filename

Convert the workflow name to kebab-case for the filename:
- "Invoice Data Extraction" → `invoice-data-extraction.json`
- "Gmail Invoice Processor" → `gmail-invoice-processor.json`
- Remove special characters, lowercase, replace spaces with hyphens

### 3. Save the Workflow File

Save the workflow JSON to: `n8n-workflows/<filename>.json`

Ensure the JSON is properly formatted (pretty-printed with 2-space indentation).

### 4. Analyze the Workflow

From the nodes, determine:

**Services Used** - Map node types to friendly names:
| Node Type | Service Name |
|-----------|--------------|
| `n8n-nodes-base.gmail` | Gmail |
| `n8n-nodes-base.gmailTrigger` | Gmail |
| `n8n-nodes-base.googleSheets` | Google Sheets |
| `n8n-nodes-base.googleDrive` | Google Drive |
| `n8n-nodes-base.googleDriveTrigger` | Google Drive |
| `n8n-nodes-base.googleDocs` | Google Docs |
| `n8n-nodes-base.slack` | Slack |
| `n8n-nodes-pdfvector.pdfVector` | PDF Vector |
| `n8n-nodes-base.httpRequest` | HTTP/API |
| `n8n-nodes-base.webhook` | Webhook |
| `n8n-nodes-base.code` | Code (JavaScript) |
| `n8n-nodes-base.if` | Conditional Logic |
| `n8n-nodes-base.switch` | Switch/Router |
| `n8n-nodes-base.merge` | Merge |
| `n8n-nodes-base.splitInBatches` | Batch Processing |

**Workflow Flow** - Trace the connections between nodes to describe the step-by-step process.

**Target Users** - Based on the workflow's purpose, identify who would benefit.

### 5. Select Appropriate Emoji

Choose based on workflow category:
- 📄 Documents/Files
- 💰 Finance/Invoices
- 📧 Email
- 🏥 Healthcare
- ⚖️ Legal
- 🏠 Real Estate
- 🎓 Education
- 👤 HR/Recruitment
- 🚚 Logistics
- 🔧 General/Other

### 6. Update README.md

#### A. Add New Workflow Section

Insert a new `<details>` section under `### Available Workflows` in README.md.

**IMPORTANT**: Add the new section BEFORE the `### How to Import` section, after the last existing `</details>` tag.

Use this exact template:

```html
<details>
<summary><strong>{EMOJI} {Workflow Name}</strong> - {Short description} | <a href="https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/{filename}.json">⬇️ Download</a></summary>

{Opening paragraph describing value proposition - 2-3 sentences explaining what this workflow does and why it's valuable}

#### Who is this for?
- {Target user 1}
- {Target user 2}
- {Target user 3}

#### How it works
1. **{Node 1 Name}** {description of what this step does}
2. **{Node 2 Name}** {description of what this step does}
3. **{Node 3 Name}** {description of what this step does}
{Continue for all significant nodes}

#### Services used
- {Service 1} ({purpose})
- {Service 2} ({purpose})

#### Setup instructions
1. Import the workflow JSON into n8n
2. Configure {credential 1} credentials
3. {Additional setup steps based on services used}
4. Activate the workflow

#### Customizing this workflow
- {Customization suggestion 1}
- {Customization suggestion 2}

</details>
```

#### B. Update the Workflow Count Badge

Find the badge in the README header:
```
![n8n Workflows](https://img.shields.io/badge/n8n-{N}_workflows-FF6D5A)
```

Increment `{N}` by 1.

Also update the count in the "Supported Platforms" table:
```
| ![n8n](https://img.shields.io/badge/-n8n-FF6D5A?style=flat&logo=n8n&logoColor=white) | Available | {N} | [`n8n-workflows/`](n8n-workflows/) |
```

## Verification Checklist

After completing the steps, verify:
- [ ] JSON file exists at `n8n-workflows/<filename>.json`
- [ ] JSON is valid and properly formatted
- [ ] README has new `<details>` section with correct format
- [ ] Download link URL is correct: `https://raw.githubusercontent.com/khanhduyvt0101/workflows/main/n8n-workflows/{filename}.json`
- [ ] Badge count is incremented
- [ ] Table count matches badge count
- [ ] Emoji matches workflow category
- [ ] All services used are listed
- [ ] Setup instructions mention all required credentials

## Example Output

When you complete this skill, inform the user:

```
✅ Added workflow: {Workflow Name}

- Saved to: n8n-workflows/{filename}.json
- Services: {list of services}
- README updated with documentation
- Workflow count: {old} → {new}
```
