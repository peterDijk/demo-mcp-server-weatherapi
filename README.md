# Demo MCP Server - Weather API

A demonstration server implementing the [Model Context Protocol (MCP)](https://github.com/modelcontextprotocol/mcp) that integrates with the National Weather Service API to provide weather data through MCP tools.

## Overview

This project showcases how to build an MCP server that wraps an external API (in this case, the NWS API at api.weather.gov) to provide structured weather data to MCP clients. The server exposes tools that can be used by MCP-compatible clients to retrieve weather forecasts and alerts.

## Features

- **MCP Server Implementation**: Full implementation of the Model Context Protocol server
- **Weather Tools**:
  - `get-forecast`: Retrieve weather forecasts for a specific location using latitude and longitude
  - `get-alerts`: Get active weather alerts for a specific U.S. state
- **Multiple Transport Options**:
  - HTTP with streaming responses
  - Server-Sent Events (SSE) transport (commented out by default)

## Prerequisites

- Node.js v18+ (v22 recommended)
- npm

## Installation

Clone the repository and install dependencies:

```bash
git clone <repository-url>
cd demo-mcp-server-weatherapi
npm install
```

## Running the Server

### Using npm

```bash
# Start the MCP server
npm start

# Start with MCP Inspector for development
npm run dev
```

The server will be available at http://localhost:3002/mcp.

### Using Docker

Build and run using Docker Compose:

```bash
docker-compose up --build
```

The server will be available at http://localhost:3000/mcp.

## API Usage

The server implements the Model Context Protocol and exposes the following tools:

### Get Weather Forecast

Retrieves a weather forecast for a geographic location.

```json
{
  "method": "tool",
  "params": {
    "name": "get-forecast",
    "parameters": {
      "latitude": 37.7749,
      "longitude": -122.4194
    }
  }
}
```

### Get Weather Alerts

Retrieves active weather alerts for a U.S. state.

```json
{
  "method": "tool",
  "params": {
    "name": "get-alerts",
    "parameters": {
      "state": "CA"
    }
  }
}
```

## MCP Inspector

During development, you can use the MCP Inspector to visualize and interact with your MCP server. Run:

```bash
npm run dev
```

The MCP Inspector will be available in your browser, allowing you to test the various tools.

## Project Structure

- `src/index.ts` - Application entry point
- `src/mcp-server.ts` - MCP server implementation with tool definitions
- `src/weather-api.ts` - Weather API integration with the NWS API
- `src/stream-http-server.ts` - HTTP server with streaming support
- `src/sse-server.ts` - Server-Sent Events (SSE) transport implementation

## Docker Support

The project includes Docker support for easy deployment:

- `Dockerfile` - Container definition
- `docker-compose.yml` - Service configuration

## License

ISC

## Author

Peter van Dijk