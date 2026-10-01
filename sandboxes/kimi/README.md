# Kimi Code CLI Sandbox

A community sandbox with [Kimi Code CLI](https://github.com/MoonshotAI/kimi-cli) pre-installed for AI-assisted development.

## What is Kimi Code CLI

Kimi Code CLI is an AI agent that runs in the terminal, helping you complete software development tasks and terminal operations. It can:

- Read and edit code
- Execute shell commands
- Search and fetch web pages
- Autonomously plan and adjust actions during execution

## Build

```bash
docker build -t kimi-sandbox .
```

To build against a specific base image:

```bash
docker build -t kimi-sandbox --build-arg BASE_IMAGE=ghcr.io/nvidia/openshell-community/sandboxes/base:latest .
```

## Usage

Create a sandbox with Kimi pre-installed. Bare `--from kimi` resolves against the
upstream NVIDIA community registry, where this sandbox is not published, so use the
full image reference published by this fork:

```bash
openshell sandbox create --from ghcr.io/asyncsquadlabs/openshell-community/sandboxes/kimi:latest
```

Alternatively, point the community registry override at the fork's namespace and keep
the short form:

```bash
export OPENSHELL_COMMUNITY_REGISTRY=ghcr.io/asyncsquadlabs/openshell-community/sandboxes
openshell sandbox create --from kimi
```

The upstream home for community sandboxes is
[NVIDIA/OpenShell-Community](https://github.com/NVIDIA/OpenShell-Community), where this
sandbox may be contributed later.

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

This sandbox ships its own `policy.yaml` rather than inheriting the default OpenShell policy. Network access is proxied and restricted to the Kimi/Moonshot API endpoints (`api.moonshot.cn`, `kimi.moonshot.cn`, and `*.moonshot.cn` on port 443); all other network traffic is blocked. Note that under the default OpenShell policy all network access is blocked, so it is these allow rules that let Kimi Code CLI reach its API. If you configure Kimi to use a different provider, add its endpoints to the network policy.

## See Also

- [Kimi Code CLI GitHub](https://github.com/MoonshotAI/kimi-cli)
- [Kimi Documentation](https://moonshotai.github.io/kimi-cli/)
