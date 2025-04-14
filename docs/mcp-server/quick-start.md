---
sidebar_position: 1
---

# Quick start

## Prerequisites

Before you begin, ensure you have the following installed:
- Node.js (20 or later recommended)
- pnpm (`npm install -g pnpm`)
- Git

## Get started
The whole thing consists of two services that we need to run.

1.  **Clone the repository:**
    ```sh
    git clone https://github.com/mateuszm-arianelabs/hedera-mcp-server.git
    cd hedera-mcp-server
    ```

2.  **Set up environment variables in packages:**
    - You need to copy the .env.example file and create .env from it in two locations:
        - packages/langchain-proxy
        - packages/mcp-server

    Edit the `.env` file and fill in the required configuration values (e.g., Hedera keys, network details).
    ```shell
    API_URL=                  # url to langchain proxy endpoint
    PORT=                     # port on which MCP server will be started
    MCP_AUTH_TOKEN=           # array of accepted tokens separated by comas
    LANGCHAIN_PROXY_TOKEN=    # token for accessing the Langchain proxy
    ```

3.  **Install dependencies:**
    ```sh
    pnpm install
    ```

4.  **Start Lang chain Proxy Service**
    ```
    pnpm run dev:lc
    ```
    (Or `pnpm start` for production mode, if configured).
5.  **Run the mcp server:**
    ```sh
    pnpm run dev:mcp
    ```
    (Or `pnpm start` for production mode, if configured).

6. Enjoy [How to use](/mcp-server/how-to-use)