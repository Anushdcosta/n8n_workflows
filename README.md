# n8n Workflows Repository

This repository contains exported n8n workflow JSON files created from a live automation setup. The README is based on the workflow content and discovered integrations rather than an unrelated template file.

## Included Workflows

- `Main_Workflow.json`
  - Central AI assistant workflow
  - Uses webhooks, AI models, database memory, and external workflow execution
  - Contains request routing, search integration, parent mode controls, and scheduler calls
  - Integrates with:
    - Postgres memory nodes
    - Ollama / Llama3 / Mistral model nodes
    - Webhook triggers
    - HTTP APIs

- `Parent Mode Chat.json`
  - Parent-mode chat controller workflow
  - Runs on execute-workflow triggers and webhook input
  - Uses conditional routing, webhooks, HTTP requests, and MySQL database actions
  - Includes logic for monitoring child progress, updating schedules, and responding to webhook events

- `Scheduler_Tool.json`
  - Scheduling / availability workflow
  - Accepts task and deadline inputs for schedule generation
  - Generates available time slots from busy schedules
  - Uses MySQL queries, JavaScript code nodes, HTTP requests, and webhooks
  - Designed to integrate with external execution triggers and schedule synchronization APIs

## How to Use

1. Open your n8n instance.
2. Import each JSON file using the n8n import workflow feature.
3. Configure required credentials in n8n before activation:
   - `Postgres account`
   - `MySQL account 2`
   - `Ollama account`
4. Update webhook URLs and HTTP targets for your environment.

## Important Configuration Notes

- The workflows reference internal URLs and services such as:
  - `http://100.93.185.22:8080/n8n_trigger`
  - `http://100.111.120.112:5001/api/trigger`
  - `http://100.111.120.112:5002/api/speak`
  - `http://172.17.0.1:11434/api/generate`
  - `http://172.17.0.1:8080/search?format=json`
  - `http://localhost:5678/webhook/thought_dump`

- These addresses are likely environment-specific and should be replaced with your own service endpoints.

## What This Repository Is

- A set of exported workflow definitions for n8n
- Not a web application source repo
- Intended to be imported into n8n and adapted to your own infrastructure

## Recommended Next Steps

- Review each workflow after import to verify node credentials and endpoint values.
- Replace hard-coded HTTP service URLs with your deployment-specific addresses.
- Test the webhooks and scheduled flows in an isolated environment before use.

## Notes

- Workflow file names are the source of truth, and this README was built from the actual file exports.
- No generic README template content is included.
