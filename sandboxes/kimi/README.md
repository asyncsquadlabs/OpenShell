# Kimi Code CLI Sandbox

A community sandbox with [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli) pre-installed for AI-assisted development.

## What is Kimi Code CLI

Kimi Code CLI is an AI agent that runs in the terminal, helping you complete software development tasks and terminal operations. It can:

- Read and edit code
- Execute shell commands
- Search and fetch web pages
- Autonomously plan and adjust actions during execution

## Usage

Create a sandbox with Kimi pre-installed:

```bash
openshell sandbox create --from kimi
```

Once inside the sandbox, start Kimi:

```bash
kimi
```

On first launch, configure your API source:

```
/login
```

See the [Kimi Code CLI documentation](https://moonshotai.github.io/kimi-cli/) for more details.

## Included Tools

- `kimi` - Interactive AI chat and task execution
- `kimi web` - Browser UI for graphical interface
- All tools from the base sandbox (curl, iproute2, iptables, etc.)

## Policy

This sandbox inherits the default OpenShell policy. You may need to add network policies for Kimi's API endpoints depending on your provider (e.g., `api.moonshot.cn` for Kimi Code).

## See Also

- [Kimi Code CLI GitHub](https://github.com/MoonshotAI/kimi-cli)
- [Kimi Documentation](https://moonshotai.github.io/kimi-cli/)
