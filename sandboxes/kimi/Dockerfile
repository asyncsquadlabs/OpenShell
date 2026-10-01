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
# The base image already includes uv and Python, so we just need to install the tool.
# By default uv puts the tool venv in ~/.local/share/uv/tools and the `kimi` shim
# in ~/.local/bin — both under /root (mode 0700), which the sandbox user cannot
# traverse, and the shim's interpreter shebang points into the tool venv. Install
# into shared locations instead (same idea as the base image copying the Claude
# CLI to /usr/local/bin):
#   UV_TOOL_DIR      -> tool venv, under the shared uv state dir on /sandbox
#   UV_TOOL_BIN_DIR  -> the `kimi` shim; /usr/local/bin is already on PATH
# Set inline rather than via ENV so a runtime `uv tool install` by the sandbox
# user still writes to user-owned locations instead of root-owned /usr/local/bin.
# uv also downloads the CPython 3.13 toolchain into UV_PYTHON_INSTALL_DIR
# (/sandbox/.uv/python, inherited from the base image) as root, so hand
# /sandbox/.uv back to the sandbox user, mirroring the base image's chown of
# /sandbox/.venv.
RUN UV_TOOL_DIR="/sandbox/.uv/tools" \
    UV_TOOL_BIN_DIR="/usr/local/bin" \
    uv tool install --python 3.13 kimi-cli \
    && chown -R sandbox:sandbox /sandbox/.uv

# Copy sandbox policy
COPY policy.yaml /etc/openshell/policy.yaml

# Switch back to sandbox user
USER sandbox

# Verify installation
RUN kimi --version

# Default command (can be overridden at runtime)
CMD ["kimi"]
