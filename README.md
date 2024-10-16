# Neon AI API Documentation

## Overview
The Neon AI API allows you to interact with an AI-powered chatbot. You can send user prompts and receive responses. The API supports session management for maintaining conversation context.

### Base URLs
1. **Base 1 (Requires API Key)**:  
   `https://neonai.neonstore.tech/`
2. **Base 2 (No API Key Required)**:  
   `https://ais.snurlaelah1637617.workers.dev/`

## Authentication (Base 1)

To use **Base 1** (`neonai.neonstore.tech`), you need to include an API key in the query of your request.



---

## Endpoints

### 1. Send a Prompt

**URL:**
- **Base 1 (with API key)**:  
  `GET https://neonai.neonstore.tech/?prompt={prompt}&session={session_id}`
- **Base 2 (no API key required)**:  
  `GET https://ais.snurlaelah1637617.workers.dev/?prompt={prompt}&session={session_id}`

**Method:** `GET`

**Query (Base 1 only):**
| Query           | Value                     |
|------------------|---------------------------|
| `apiKey`  | string      |

**Query Parameters:**

| Parameter | Type   | Description                                                                                     |
|-----------|--------|-------------------------------------------------------------------------------------------------|
| `prompt`  | string | The user's message to the AI. This parameter is required.                                        |
| `session` | string | (Optional) The session ID for maintaining conversation context. If not provided, a new session is created. |

**Example Request (Base 1):**
```plaintext
GET https://neonai.neonstore.tech/?prompt=What%20is%20your%20name&session=b0d8b4c1-42b2-4cd7-b662-8b3a4bf4d4a0&apiKey=key-here
```

**Example Request (Base 2):**
```plaintext
GET https://ais.snurlaelah1637617.workers.dev/?prompt=Tell%20me%20a%20joke&session=b0d8b4c1-42b2-4cd7-b662-8b3a4bf4d4a0
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
          "content": "What is your name?"
        }
      ]
    },
    "response": {
      "response": "Hello! My name is Neon AI, created by Neon Corporation."
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

---

## Usage Example

1. **Sending a Prompt:**

   You can send a prompt to the AI by making a GET request to the API endpoint. Here is an example for **Base 1** (with an API key):

   ```plaintext
   GET https://neonai.neonstore.tech/?prompt=Tell%20me%20a%20joke&apiKey=api-key
   ```

   For **Base 2** (no API key required):

   ```plaintext
   GET https://ais.snurlaelah1637617.workers.dev/?prompt=Tell%20me%20a%20joke
   ```

2. **Receiving the Response:**

   After sending the prompt, you will receive a JSON response containing the session ID, the input messages, and the AI's response, as shown in the response format section.

---

## Error Handling

- If the `prompt` parameter is missing, the API will return an error indicating that the prompt is required.
- If an invalid session ID is provided, the API may respond with a message indicating that the session is not recognized.

---

## Monthly API Key Limit

For **Base 1** (`neonai.neonstore.tech`), each API key has a limit of **50 requests per month**. This limit resets on the first day of each month.

### Generate API Key

To generate a new API key, make a request to the following endpoint:

**URL:**  
```
GET https://neonai.neonstore.tech/generate
```

The response will include your new API key, which can be used for requests to **Base 1**.

