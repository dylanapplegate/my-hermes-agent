# Local Firecrawl Setup

This directory contains a docker-compose setup to run Firecrawl locally.

## Setup

1. Copy the example environment variables:
   ```bash
   cp firecrawl/.env.example firecrawl/.env
   ```
   *Note: Update `BULL_AUTH_KEY` and database credentials in `.env` for production use.*

2. Launch the infrastructure:
   ```bash
   docker compose -f firecrawl/docker-compose.yaml up -d
   ```

3. Access the service:
   - API: `http://localhost:3002`
   - Bull Queue Manager: `http://localhost:3002/admin/CHANGEME/queues` (ensure `CHANGEME` matches your `BULL_AUTH_KEY`)

## Verification

Test the crawl endpoint:
```bash
curl -X POST http://localhost:3002/v1/crawl \
    -H 'Content-Type: application/json' \
    -d '{
      "url": "https://firecrawl.dev"
    }'
```

## MCP Integration

To use Firecrawl in your MCP-compatible tools (like Cursor, Claude Desktop, or Windsurf), use the configuration provided in `firecrawl/mcp-config.json`.

If configuring manually, ensure your MCP server command is:
`npx -y firecrawl-mcp`

And set the environment variable:
`FIRECRAWL_API_URL=http://localhost:3002`

If you have issues, check the Docker logs:
```bash
docker compose -f firecrawl/docker-compose.yaml logs -f
```
