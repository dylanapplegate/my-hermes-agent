# Hermes Agent - OpenCode Configuration

## Agent Roles

- **Prometheus**: Strategic planner. Creates work plans. Does NOT write code.
- **Sisyphus/Build agents**: Implementers. Execute plans, write code.

Running `/start-work` triggers transition from planning to execution.

## GitHub Flow

- **Main is protected** — do not push directly
- **Atomic commits required** — one logical change per commit
- Work on feature branches, PR into main

## MCP Servers (Configured)

### firecrawl-mcp
- **Purpose**: Web scraping, search, crawling, page interaction
- **Command**: `npx -y firecrawl-mcp`
- **API URL**: `http://localhost:3002`
- **API Key**: `not-needed-locally` (local dev)

### docker
- **Command**: `npx -y mcp-server-docker`
- **Host**: `unix:///var/run/docker.sock`

## Local Firecrawl Stack

```bash
# Setup
cp firecrawl/.env.example .env

# Launch (from repo root)
docker compose -f firecrawl/docker-compose.yaml up -d

# Verify
curl -X POST http://localhost:3002/v1/crawl -H 'Content-Type: application/json' -d '{"url": "https://example.com"}'

# Logs
docker compose -f firecrawl/docker-compose.yaml logs -f
```

Services: Firecrawl API, PostgreSQL, Redis, RabbitMQ, Playwright service.

## Skills

Skills are installed globally at `~/.agents/skills/`. Available skills include:
- `firecrawl-*`: Web scraping, search, crawl, download, interact capabilities
- `frontend-ui-ux`, `playwright`, `git-master`: Built-in OpenCode skills
- `caveman`: Ultra-compressed communication mode

## Reference Documentation

`docs/reference/hermes-doc-pack.md` contains packed Hermes Agent documentation from NousResearch/hermes-agent.

## Development Notes

- `.env` is gitignored — copy from `.env.example`
- This repo is a config layer, not a code project — minimal build/test setup
