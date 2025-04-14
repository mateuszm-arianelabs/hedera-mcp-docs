---
sidebar_position: 1
---

# Langchain proxy

Under normal usage, you won’t need the API described below. However, if for any reason you'd like to run only the Langchain wrapper—which enables interaction with Hedera—and access it via a standard REST API, then this section is for you.


## Authorization
The endpoints (currently only one is available) are secured using basic token-based authorization. In the environment variables of the Langchain wrapper, you need to set the `LANGCHAIN_PROXY_TOKEN` variable, which represents your access token. You can use any value you like or generate one yourself.

To access the wrapper, every request must include the `X-LANGCHAIN-PROXY-TOKEN` header with the token value. If this header is missing or incorrect, the server will return an error.

## Available endpoints
- `/interact-with-heder` - At the moment, this is the only available endpoint, and behind it lies the full Langchain setup powered by an LLM that determines which action should be taken based on your input. 

Aside from the authorization header, the endpoint accepts a single field: `fullPrompt`. This field contains the entire prompt describing the action to be performed on Hedera.

__Expected body__:
```json
{
    "fullPrompt": string
}
```

## Response

Below you'll find two possible responses from the server, depending on whether an error occurs during the process.
```typescript
interface SuccessResponse<T> {
    success: true,
    data: T
}
```
```typescript
interface ErrorResponse {
    success: false,
    error: string
}
```

## Example

__Request:__
```json
{
    "fullPrompt": "Create for me token MTK MyToken with 10 decimals and 10000 initial"
}
```

__Response:__
```json
{
    "success": true,
    "data": {
        "status": "success",
        "message": "Token creation successful",
        "initialSupply": 10000,
        "tokenId": "0.0.5856550",
        "decimals": 10,
        "solidityAddress": "0000000000000000000000000000000000595d26",
        "txHash": "0.0.4515756@1744631044.874527254"
    }
}
```
