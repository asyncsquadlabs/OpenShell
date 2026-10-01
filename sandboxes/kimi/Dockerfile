# SPDX-FileCopyrightText: Copyright (c) 2025-2026 NVIDIA CORPORATION & AFFILIATES. All rights reserved.
# SPDX-License-Identifier: Apache-2.0

# Kimi Code CLI Sandbox
#
# A community sandbox with Kimi Code CLI pre-installed for AI-assisted development.
# Kimi is an AI agent that runs in the terminal, helping with code editing,
# project exploration, and task automation.
#
# Usage: openshell sandbox create --from kimi

FROM ghcr.io/nvidia/openshell-community/sandboxes/base:latest

USER root

# Install Kimi Code CLI via uv
# The base image already includes uv and Python, so we just need to install the tool
RUN uv tool install --python 3.13 kimi-cli

# Ensure the sandbox user can access the installed tool
# uv installs tools to ~/.local/bin by default
ENV PATH="/root/.local/bin:${PATH}"

# Copy sandbox policy
COPY policy.yaml /etc/openshell/policy.yaml

# Switch back to sandbox user
USER sandbox

# Verify installation
RUN kimi --version

# Default command (can be overridden at runtime)
CMD ["kimi"]
