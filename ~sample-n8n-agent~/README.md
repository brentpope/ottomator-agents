# Base Sample Agent

Author: [Cole Medin](https://www.youtube.com/@ColeMedin)

This is a sample n8n workflow that demonstrates the minimal required components to build an agent for the Live Agent Studio. It serves as a template and reference implementation for creating new agents.

## Core Components

1. **Webhook Endpoint**
   - Accepts POST requests with authentication
   - Processes incoming queries with user and session information
   - Provides secure communication via header authentication

2. **Input Processing**
   - Extracts key fields from incoming requests:
     - query: The user's question or command
     - user_id: Unique identifier for the user
     - request_id: Request tracking ID
     - session_id: Current session identifier

3. **Database Integration**
   - Uses Supabase for message storage
   - Records both user messages and AI responses
   - Maintains conversation history with metadata

4. **Response Handling**
   - Structured response format for consistency
   - Includes success/failure status
   - Returns formatted responses via webhook

## Workflow Structure

1. **Webhook Node**
   - Entry point for all requests
   - Validates authentication headers (optional, we can add once we host for you on the studio)
   - Routes incoming POST requests

2. **Prep Input Fields Node**
   - Extracts and formats input data
   - Validates required fields
   - Prepares data for processing

3. **Database Nodes**
   - "Add User Message to DB": Records incoming user queries
   - "Add AI Message to DB": Stores AI responses

4. **Output Preparation**
   - Sets success status
   - Formats response data
   - Ensures consistent output structure

## Credentials

1. **Header Auth**
   - Used for webhook authentication
   - Ensures secure communication

2. **Supabase API**
   - Required for database operations
   - Stores conversation history

   These credentials will be swapped over to our own once we host the agent for you!

## Usage

1. Import this workflow as a template for new agents
2. Configure the required credentials:
   - Set up header authentication (optional, we can add once we host for you on the studio)
   - Configure Supabase connection
3. Customize the workflow by adding:
   - Additional processing nodes
   - Specialized AI model integrations
   - Custom business logic

## Message Format

### Input
```json
{
    "query": "User's question or command",
    "user_id": "unique-user-identifier",
    "request_id": "request-tracking-id",
    "session_id": "conversation-session-id"
}
```

### Output
```json
{
    "success": true,
    "output": "AI response content",
    "data": "Additional response data"
}
```

## Contributing

This agent is part of the oTTomator agents collection. For contributions or issues, please refer to the main repository guidelines.