# Google Embedding UTCP Manual

This project provides a UTCP (Universal Tool Calling Protocol) manual for the Google Gemini embedding model. This manual allows any UTCP-compliant client to generate text embeddings using the Gemini API without requiring any custom wrapper code.

## About the Google Embedding Model

Text embeddings are numerical representations of text that capture semantic meaning. These vector representations are crucial for a wide variety of NLP tasks, including:

-   **Semantic Search**: Finding text that is conceptually similar, not just keyword-matched.
-   **Classification**: Categorizing text into predefined labels.
-   **Clustering**: Grouping similar texts together to identify trends.
-   **Retrieval Augmented Generation (RAG)**: Enhancing language model outputs with factual information retrieved from a knowledge base.

The Google Gemini embedding model (`gemini-embedding-001`) is a state-of-the-art model that generates high-dimensional embeddings (3072 dimensions by default) to power these applications.

## About the Universal Tool Calling Protocol (UTCP)

UTCP is a modern, flexible, and scalable standard for defining and interacting with tools across various communication protocols. Its core philosophy is to **describe, not wrap**.

Instead of building and maintaining custom adapter servers for every tool, UTCP allows developers to create a simple "manual" (a `.json` file) that teaches a client how to call the tool's native endpoint directly. This approach has several key benefits:

-   **No Wrapper Tax**: Eliminates the overhead of building and deploying adapter services.
-   **Direct Communication**: Clients call tools directly, reducing latency.
-   **Leverages Existing Infrastructure**: Uses the tool's native authentication, security, and rate-limiting.
-   **Protocol Agnostic**: Works with any communication protocol (HTTP, WebSockets, CLI, gRPC, etc.).

## Usage

To use this manual, you will need a UTCP client. The client will load the `google-embedding-utcp-manual.utcp.json` file to discover the `embed_content` tool.

### Calling the `embed_content` Tool

Here is an example of how a client would call the `embed_content` tool defined in this manual:

```json
{
  "tool": "embed_content",
  "inputs": {
    "model": "gemini-embedding-001",
    "contents": ["Hello world"]
  }
}
```

### Authentication

The `tool_provider` in the `google-embedding-utcp-manual.utcp.json` file uses a variable for the API key: `${GEMINI_API_KEY}`. Your UTCP client must be configured to replace this variable with your actual Gemini API key.
