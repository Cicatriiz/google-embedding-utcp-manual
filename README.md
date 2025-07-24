# Google Embedding UTCP Manual

This project provides a UTCP (Universal Tool Calling Protocol) manual for the Google Gemini embedding model. This manual allows any UTCP-compliant client to generate text embeddings using the Gemini API.

## Usage

To use this manual, you will need a UTCP client. The client will load the `google-embedding-utcp-manual.utcp.json` file to discover the `embed_content` tool.

### Calling the `embed_content` Tool

Here is an example of how to call the `embed_content` tool:

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

The `tool_transport` in the `google-embedding-utcp-manual.utcp.json` file uses a variable for the API key: `${GEMINI_API_KEY}`. Your UTCP client must be configured to replace this variable with your actual Gemini API key.
