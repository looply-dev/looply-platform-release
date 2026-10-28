# Looply Agent Releases

This repository distributes the Looply Agent (`looply-agent`) for macOS and Linux on arm64 and x64. It contains release packages only. Looply source code is not in this repository.

## Install

Copy the installation command from Looply Web → Agents. The command has this form:

```bash
curl -fsSL https://github.com/looply-dev/looply-platform-release/releases/latest/download/install-agent.sh |
  sh -s -- --server https://your-looply.example.com --scope personal
```

You do not need a GitHub account or the GitHub CLI. The installer:

1. Detects your OS and CPU.
2. Downloads the platform archive and its `.sha256` file from the latest release.
3. Verifies the SHA-256 checksum and the archive paths.
4. Installs the Agent to `~/.local/share/looply-agent` and the `looply-agent` command to `~/.local/bin`.
5. Starts `looply-agent setup` for pairing. Setup reads input from `/dev/tty`, so it works through a pipe.

To install a specific or pre-release version, add `--version agent-v<version>`.

## Upgrade

1. Wait until in-progress work finishes.
2. Stop the daemon: `looply-agent stop`.
3. Run the installation command above with `--upgrade`. Your configuration and work data stay in place.
4. Start the daemon again, and restart or reconnect the MCP in your clients.

## Manual download

Download `looply-agent-<platform>.tar.gz` and its `.sha256` file from [Releases](https://github.com/looply-dev/looply-platform-release/releases). Verify the checksum, extract the archive, and run `sh looply-agent/install.sh --server <Looply HTTPS origin>`.
