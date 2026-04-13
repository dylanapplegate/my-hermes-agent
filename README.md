# Hermes Agent

This repository is a configuration and orchestration layer for Model Context Protocol (MCP) servers.

## Agent Roles

- **Prometheus**: The Strategic Planner. Responsible for creating work plans. Prometheus does not write code.
- **Sisyphus/Build agents**: The Implementers. Responsible for executing plans and writing code.

Running `/start-work` triggers the transition from planning to execution.
