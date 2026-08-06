# AI Registration Workflow

AI-powered n8n workflow that collects team data, assigns ratings, generates personalized poems using Google Gemini, and stores everything in Airtable.

## Features

- Collects team member information via n8n triggers (forms, webhooks, or manual triggers)
- Assigns ratings/metrics using a lightweight scoring step
- Generates personalized poems or messages using Google Gemini (LLM)
- Stores collected data, ratings, and generated text in Airtable

## Prerequisites

- n8n instance (self-hosted or n8n.cloud)
- Airtable account and an API key
- Google Cloud project / access to Google Gemini API (or compatible LLM access)
- Node.js (for local development/tools if applicable)

## Environment variables

Set the following environment variables in your n8n credentials or deployment environment:

- AIRTABLE_API_KEY - Your Airtable API key
- AIRTABLE_BASE_ID - The Airtable Base ID where data will be stored
- AIRTABLE_TABLE_NAME - (optional) Table name; default: `Registrations`
- GEMINI_API_KEY - API key or credentials for Google Gemini (or the LLM provider used)
- N8N_WEBHOOK_URL - (optional) Public URL for n8n webhooks if using webhooks

## Setup

1. Import the n8n workflow JSON file into your n8n instance (look for a `workflows/` or `exports/` folder in this repo).
2. Create an Airtable base with fields for name, email, role, rating, poem, timestamp, and any other metadata you need.
3. Configure the n8n credentials:
   - Airtable credentials using `AIRTABLE_API_KEY`
   - HTTP Request / Google API credentials for calling Google Gemini (use `GEMINI_API_KEY` or the credential type supported by your n8n instance)
4. Update any workflow node environment variables or parameter values to match your Airtable table and field names.

## Usage

- Trigger the workflow via the configured trigger (webhook, form, schedule, or manual run).
- The workflow will collect submitted data, compute a rating, call the LLM to generate a poem, and save the result to Airtable.

## Development

- If you add or modify the exported workflow JSON, re-import it into n8n to update the flow.
- Keep secrets out of the repo; use environment variables or n8n credentials for API keys.

## Contributing

Contributions are welcome. Open an issue or a pull request with suggested improvements, bug fixes, or workflow enhancements.

## License

Include your preferred license here (e.g., MIT). If you don't have one yet, consider adding an `LICENSE` file.

