# Configuración del MCP Slack Feedback

## 1. Instalación

```bash
npm install -g git+https://github.com/GailenTech/claude-mcp-slack-feedback.git
```

## 2. Configuración en Claude

Edita tu archivo de configuración de Claude Desktop. La ubicación depende de tu sistema:

- **macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
- **Windows**: `%APPDATA%\Claude\claude_desktop_config.json`
- **Linux**: `~/.config/Claude/claude_desktop_config.json`

Añade el servidor MCP a la sección `mcpServers`:

```json
{
  "mcpServers": {
    "claude-mcp-slack-feedback": {
      "command": "node",
      "args": [
        "/usr/local/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"
      ],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-tu-token-aqui",
        "SLACK_WORKSPACE_URL": "tu-workspace.slack.com"
      }
    }
  }
}
```

## 3. Variables de Entorno Requeridas

- `SLACK_BOT_TOKEN`: Token del bot de Slack (empieza con xoxb-)
- `SLACK_WORKSPACE_URL`: URL de tu workspace (ej: gailen.slack.com)

## 4. Permisos del Bot de Slack

El bot necesita estos OAuth scopes:
- `channels:write` - Crear canales
- `chat:write` - Enviar mensajes
- `channels:read` - Listar canales
- `users:read` - Obtener info de usuarios
- `users:read.email` - Emparejar por email

## 5. Verificar la Instalación

Después de configurar, reinicia Claude Desktop. Las herramientas MCP deberían aparecer:
- `mcp__claude-mcp-slack-feedback__setup_slack_config`
- `mcp__claude-mcp-slack-feedback__ask_feedback`
- `mcp__claude-mcp-slack-feedback__inform_slack`
- `mcp__claude-mcp-slack-feedback__update_progress`
- `mcp__claude-mcp-slack-feedback__get_responses`

## Ejemplo de Configuración Completa

```json
{
  "mcpServers": {
    "claude-mcp-slack-feedback": {
      "command": "node",
      "args": [
        "/usr/local/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"
      ],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-TU-TOKEN-AQUI",
        "SLACK_WORKSPACE_URL": "gailen.slack.com"
      }
    }
  }
}
```