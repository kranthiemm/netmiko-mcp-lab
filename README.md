# netmiko-mcp-lab

Example configs for testing [netmiko-mcp](https://pypi.org/project/netmiko-mcp/)
(an MCP server for Netmiko) with Claude Desktop against a lab device.

## Files

| Example file | Real file (git-ignored) |
|---|---|
| netmiko-mcp.example.yml | .netmiko-mcp.yml |
| netmiko.example.yml | .netmiko.yml |
| commands.example.yml | commands.yml |
| claude_desktop_config.example.json | merge into Claude Desktop config |

Copy each example, drop ".example", and fill in real values.
The real files hold credentials and are listed in .gitignore. Never commit them.

## Setup

1. Install: `uv tool install netmiko-mcp`
2. Find the executable: `which netmiko-mcp` (use the full path in the Claude Desktop config)
3. Create the three real files in this folder from the examples.
4. Use ABSOLUTE paths in `.netmiko-mcp.yml`.
5. Add the `netmiko` block to `~/Library/Application Support/Claude/claude_desktop_config.json`
   inside `mcpServers`, with `NETMIKO_MCP_CONFIG` set to the absolute path of `.netmiko-mcp.yml`.
6. Quit Claude Desktop completely (Cmd+Q) and reopen it.

## Test prompts

1. Use the netmiko MCP ping tool. Expect `pong`.
2. List the devices in my Netmiko inventory.
3. Run `show version` on sandbox-xe1 and return JSON.
4. Run `show clock` on sandbox-xe1. Expect a refusal if it is not whitelisted.

## Gotchas

- Quote passwords in single quotes in .netmiko.yml.
- Claude Desktop does not read your shell PATH, so use the full executable path.
- Keep the whitelist to read-only show commands and lab devices only.
