# EzgiAI Windows Agent

Windows Service agent for secure remote SQL access via EzgiAI cloud platform.

## Features

- ✅ Windows Service with automatic startup
- ✅ Modern configuration UI (Avalonia)
- ✅ Multi-database support (SQL Server, PostgreSQL)
- ✅ Secure outbound-only WebSocket connection
- ✅ Read-only query execution
- ✅ Real-time connection status
- ✅ Automatic updates from GitHub
- ✅ Comprehensive logging

## Download

Download the latest release from [Releases](https://github.com/raifemre/ezgiai-windows-agent-public/releases)

## Installation

See [DEPLOYMENT_INSTRUCTIONS.md](releases/v0.1.0/DEPLOYMENT_INSTRUCTIONS.md) for detailed installation steps.

### Quick Start

1. Download and extract the release package
2. Run `WindowsAgent.UI.exe` as Administrator
3. Click "Install Service"
4. Configure settings (Agent ID, Organization ID, API Key)
5. Add database profiles
6. Click "Save Configuration"
7. Click "Start Service"

## Requirements

- Windows Server 2016 or later
- Administrator privileges for service installation
- Outbound HTTPS access (port 443)

## Architecture

```
┌─────────────────┐
│  Configuration  │
│      UI         │ ◄─── Named Pipes (IPC)
└─────────────────┘
         ▲
         │
         ▼
┌─────────────────┐
│ Windows Service │ ◄─── WebSocket (WSS)
│     Agent       │      to Cloud Relay
└─────────────────┘
         │
         ▼
┌─────────────────┐
│   Databases     │
│ (MSSQL/Postgres)│
└─────────────────┘
```

## Support

For issues or questions, visit [GitHub Issues](https://github.com/raifemre/ezgiai-windows-agent-public/issues)

## License

Proprietary - © 2025 EzgiAI
