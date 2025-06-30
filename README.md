# Claude MCP Slack Feedback

MCP server that enables Claude to request human feedback through Slack during task execution.

## Installation

### Method 1: Using Claude CLI (Recommended)

```bash
# Install globally
npm install -g git+https://github.com/GailenTech/claude-mcp-slack-feedback.git

# Add to Claude Code
claude mcp add-json claude-mcp-slack-feedback '{
  "command": "node",
  "args": ["/opt/homebrew/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"],
  "env": {
    "SLACK_BOT_TOKEN": "xoxb-YOUR-TOKEN-HERE",
    "SLACK_WORKSPACE_URL": "your-workspace.slack.com"
  }
}'
```

Note: Replace the path with your actual npm global modules path. Find it with: `npm root -g`

### Method 2: Manual Configuration

Edit `~/.claude/mcp_settings.json`:

```json
{
  "servers": {
    "claude-mcp-slack-feedback": {
      "command": "node",
      "args": [
        "/opt/homebrew/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"
      ],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-YOUR-TOKEN-HERE",
        "SLACK_WORKSPACE_URL": "your-workspace.slack.com"
      }
    }
  }
}
```

## Slack App Setup

1. Create a new Slack app at https://api.slack.com/apps
2. Add these OAuth scopes:
   - `channels:write` - Create channels
   - `chat:write` - Send messages
   - `channels:read` - List channels
   - `users:read` - Get user info
   - `users:read.email` - Match by email
3. Install the app to your workspace
4. Copy the Bot User OAuth Token (starts with `xoxb-`)

## Usage

Once configured, Claude Code will have access to these tools:

- `mcp__claude-mcp-slack-feedback__setup_slack_config` - Initial setup
- `mcp__claude-mcp-slack-feedback__ask_feedback` - Request feedback
- `mcp__claude-mcp-slack-feedback__inform_slack` - Send updates
- `mcp__claude-mcp-slack-feedback__update_progress` - Update threads
- `mcp__claude-mcp-slack-feedback__get_responses` - Retrieve responses

## Features

- Multi-user and multi-session support
- Automatic channel creation per session
- Webhook-based real-time responses (primary)
- Polling fallback when webhooks unavailable
- Rate limiting and error handling

## Development

```bash
# Clone the repository
git clone https://github.com/GailenTech/claude-mcp-slack-feedback.git
cd claude-mcp-slack-feedback

# Install dependencies
npm install

# Build
npm run build

# Run tests
npm test

# Development mode
npm run dev
```

## License

MIT