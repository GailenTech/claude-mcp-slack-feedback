# Cómo encontrar dónde se instaló el MCP

## 1. Verificar la ruta de módulos globales de npm:
```bash
npm root -g
```

En tu caso: `/opt/homebrew/lib/node_modules`

## 2. Verificar si está instalado:
```bash
npm list -g claude-mcp-slack-feedback
```

## 3. Ver la ruta completa del ejecutable:
```bash
ls -la $(npm root -g)/claude-mcp-slack-feedback/dist/index.js
```

## Configuración para Claude Desktop

En tu archivo `~/Library/Application Support/Claude/claude_desktop_config.json`:

```json
{
  "mcpServers": {
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

Nota: La ruta exacta depende de cómo tengas configurado npm en tu sistema.