# AI Grocery Assistant

An AI-powered chat assistant for managing grocery inventory. Built with [n8n](https://n8n.io/) (an open-source workflow automation tool), it uses OpenAI's chat model to handle user queries, Google Sheets for inventory storage, and a simple memory buffer for conversation context.

## Overview
This workflow creates a conversational AI agent that:
- Responds to user queries (e.g., "How many Apples do I have in stock?").
- Retrieves inventory data from a Google Sheet.
- Updates inventory (e.g., adding stock when a user says "I have bought 5 more").
- Maintains chat history for natural interactions.

Key components from the workflow analysis:
- **Chat Trigger**: Starts the conversation with a greeting.
- **AI Agent**: Orchestrates the flow using OpenAI's GPT-4o-mini model.
- **Memory**: Uses a buffer to remember previous messages.
- **Tools**: 
  - Google Sheets integration to read rows (get stock levels).
  - Google Sheets integration to append/update rows (add to inventory).
- It handles simple inventory like item names and quantities, matching on "Item Name".

Example interaction (from screenshot):
- User: "How many Apples do I have in stock?"
- Agent: "You have 5 Apples in stock."
- User: "I have bought 5 more, add them to the inventory."
- Agent: "I have updated the inventory. You now have a total of 10 Apples in stock."


## Setup Instructions
1. **Prerequisites**:
   - n8n account (free tier works).
   - OpenAI API key (for GPT-4o-mini).
   - Google Sheets API access (OAuth2 credentials).
   - A Google Sheet with columns: "Item Name" and "Quantity in stock" (e.g., sample sheet ID: `1ewH0XHeAQCZf4jaTFUYMOpESFjueHhR45OAw6ATsscA`).

2. **Import the Workflow**:
   - Download `ai-grocery-assistant-workflow.json`.
   - In n8n, go to "Workflows" > "Import from File" and upload the JSON.
   - Configure credentials:
     - OpenAI: Add your API key.
     - Google Sheets: Set up OAuth2 and link to your sheet.

3. **Activate and Test**:
   - Activate the workflow.
   - Use the chat interface (webhook-triggered) to test queries.
   - Ensure the sheet is editable by the service account.

4. **Customization**:
   - Add more tools (e.g., for other items or operations).
   - Switch to a different LLM if needed.

## License
MIT License. Feel free to fork and improve!

## Credits
Built by Syed Danish Hussain. Inspired by n8n's AI nodes.
