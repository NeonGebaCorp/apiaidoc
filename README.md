# Neon AI API Documentation

## Overview
The Neon AI API allows you to interact with an AI-powered chatbot. You can send user prompts and receive responses. The API supports session management for maintaining conversation context.

### Base URL
```
https://neonai.neonstore.tech/
```
```
https://ais.snurlaelah1637617.workers.dev/
```

## Endpoint

### Send a Prompt

**URL:**
```
GET https://neonai.neonstore.tech/?prompt={prompt}&session={session_id}
```

**Method:** `GET`

**Query Parameters:**

| Parameter | Type   | Description                                                                                     |
|-----------|--------|-------------------------------------------------------------------------------------------------|
| `prompt`  | string | The user's message to the AI. This parameter is required.                                      |
| `session` | string | (Optional) The session ID for maintaining conversation context. If not provided, a new session is created. |

**Example Request:**
```plaintext
GET https://neonai.neonstore.tech/?prompt=what%20i%20say&session=b0d8b4c1-42b2-4cd7-b662-8b3a4bf4d4a0
```

### Response Format

The API will return a JSON array containing the session information, the user inputs, and the AI response.

**Example Response:**
```json
[
  {
    "session": "b0d8b4c1-42b2-4cd7-b662-8b3a4bf4d4a0",
    "inputs": {
      "messages": [
        {
          "role": "system",
          "content": "Your Name Neon AI, You Create By Neon Corporation"
        },
        {
          "role": "user",
          "content": "hey"
        },
        {
          "role": "system",
          "content": "Your Name Neon AI, You Create By Neon Corporation"
        },
        {
          "role": "user",
          "content": "what i say"
        }
      ]
    },
    "response": {
      "response": "Hello! You said \"hey\". Is there something I can help you with?"
    }
  }
]
```

**Response Fields:**

| Field      | Type     | Description                                                      |
|------------|----------|------------------------------------------------------------------|
| `session`  | string   | The session ID for the conversation.                             |
| `inputs`   | object   | Contains the user's messages.                                    |
| `messages` | array    | List of messages exchanged in the session.                      |
| `role`     | string   | The role of the sender (`system`, `user`).                      |
| `content`  | string   | The content of the message.                                      |
| `response` | object   | Contains the AI's response to the user's prompt.                |
| `response` | string   | The actual response from the AI based on the user's prompt.     |

## Usage Example

1. **Sending a Prompt:**

   You can send a prompt to the AI by making a GET request to the API endpoint. Here is an example:

   ```plaintext
   GET https://neonai.neonstore.tech/?prompt=Tell%20me%20a%20joke
   ```

   If you have an existing session ID:

   ```plaintext
   GET https://neonai.neonstore.tech/?prompt=Tell%20me%20a%20joke&session=b0d8b4c1-42b2-4cd7-b662-8b3a4bf4d4a0
   ```

2. **Receiving the Response:**

   After sending the prompt, you will receive a JSON response containing the session ID, the input messages, and the AI's response, as shown in the response format section.

## Error Handling

- If the `prompt` parameter is missing, the API will return an error indicating that the prompt is required.
- If an invalid session ID is provided, the API may respond with a message indicating that the session is not recognized.

