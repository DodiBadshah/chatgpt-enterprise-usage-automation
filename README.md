# chatgpt-enterprise-usage-automation
Automated ChatGPT Enterprise usage reporting pipeline built with n8n, Claude AI, and Google Sheets. Includes CI/CD via GitHub Actions.
# ChatGPT Enterprise Usage Reporting Automation

AI-powered enterprise usage reporting automation using n8n, Anthropic Claude API, and Google Sheets - with GitHub Actions CI/CD validation pipeline.

## Architecture
[Manual Trigger] --> [Mock Usage Data] --> [Claude API] --> [Extract Report Text]
|
----------------------------------
|                                |
[Google Sheets]              [HTML Report]

## What This Workflow Does

This n8n workflow simulates a ChatGPT Enterprise admin reporting pipeline:

1. **Trigger** - Runs manually or on a weekly schedule
2. **Mock Usage Data** - Simulates real ChatGPT Enterprise metrics including active users, messages sent, department breakdown, and policy violations
3. **Claude API** - Sends metrics to Anthropic Claude which generates a structured professional report with Executive Summary, Usage Highlights, Department Breakdown, and Risk Flags
4. **Extract Report Text** - Parses Claude's API response into a clean text field
5. **Google Sheets Output** - Appends the report and metrics to a Google Sheet for historical tracking
6. **HTML Report Output** - Generates a styled HTML report renderable as PDF

## Tech Stack

- **n8n** - Workflow automation platform
- **Anthropic Claude API** - AI-powered report generation (claude-haiku-4-5-20251001)
- **Google Sheets API** - Report storage and historical tracking
- **GitHub Actions** - CI/CD pipeline for workflow validation

## How To Run

### Prerequisites
- n8n cloud account (free trial at n8n.io)
- Anthropic Claude API key
- Google account with Sheets access

### Setup Steps

1. Import `chatgpt-usage-report-workflow.json` into your n8n instance
2. Add your Anthropic API key to the HTTP Request node headers
3. Connect your Google account to the Google Sheets node
4. Select your target Google Sheet
5. Click "Test workflow" to run

### Environment Variables
The following must be configured inside n8n:

| Variable | Where | Description |
|---|---|---|
| ANTHROPIC_API_KEY | HTTP Request node header | Your Claude API key |
| Google OAuth | Google Sheets node credential | Your Google account |

## CI/CD Pipeline

GitHub Actions automatically validates the workflow JSON on every push to main:

- Confirms the JSON file is valid and parseable
- Checks that no API keys are exposed in the workflow file
- Verifies required node types are present in the workflow

## Security Notes

- API keys are never stored in the repository
- The workflow JSON uses placeholder values for all credentials
- GitHub secret scanning is enabled on this repository

## Portfolio Context

Built as a demonstration of AI platform administration and workflow automation skills relevant to enterprise AI governance, usage monitoring, and reporting pipelines.
