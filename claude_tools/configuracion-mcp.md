# Configuración del MCP Slack Feedback

## 1. Instalación

```bash
npm install -g git+https://github.com/GailenTech/claude-mcp-slack-feedback.git
```

## 2. Configuración en Claude Code (CLI)

Edita tu archivo de configuración de Claude Code:

- **Ubicación**: `~/.claude/mcp_settings.json`

Añade el servidor MCP a la sección `servers`:

```json
{
  "servers": {
    "claude-mcp-slack-feedback": {
      "command": "node",
      "args": [
        "/opt/homebrew/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"
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

Después de configurar, inicia una nueva sesión de Claude Code. Las herramientas MCP deberían aparecer:
- `mcp__claude-mcp-slack-feedback__setup_slack_config`
- `mcp__claude-mcp-slack-feedback__ask_feedback`
- `mcp__claude-mcp-slack-feedback__inform_slack`
- `mcp__claude-mcp-slack-feedback__update_progress`
- `mcp__claude-mcp-slack-feedback__get_responses`

## Ejemplo de Configuración Completa

```json
{
  "servers": {
    "claude-mcp-slack-feedback": {
      "command": "node",
      "args": [
        "/opt/homebrew/lib/node_modules/claude-mcp-slack-feedback/dist/index.js"
      ],
      "env": {
        "SLACK_BOT_TOKEN": "xoxb-TU-TOKEN-AQUI",
        "SLACK_WORKSPACE_URL": "gailen.slack.com"
      }
    }
  }
}
```