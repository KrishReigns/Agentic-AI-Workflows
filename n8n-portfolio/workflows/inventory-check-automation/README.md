# Inventory Check Automation

Weekly AI-powered inventory monitor using AWS Bedrock. Reads Google Sheets, filters low-stock items, and emails alerts.

## Setup
1. Configure AWS IAM credentials for Bedrock access
2. Connect Google Sheets OAuth2 and update spreadsheet ID
3. Connect Gmail OAuth2 and update recipient email
4. Schedule runs every Monday at 9AM (configurable)
