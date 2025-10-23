# EzgiAI Windows Agent - Deployment Instructions

## 📦 Package Contents

### Agent Folder (`./agent/`)
- **EzgiAI.WindowsAgent.exe** - Windows Service executable
- **appsettings.json** - Configuration file
- DLL dependencies

### UI Folder (`./ui/`)
- **WindowsAgent.UI.exe** - Configuration UI application
- DLL dependencies

## 🚀 Installation Steps

### 1. Copy Files to Windows Machine
Copy both `agent` and `ui` folders to your Windows machine:
```
C:\Program Files\EzgiAI\
├── agent\
│   ├── EzgiAI.WindowsAgent.exe
│   ├── appsettings.json
│   └── *.dll
└── ui\
    ├── WindowsAgent.UI.exe
    └── *.dll
```

### 2. Run UI as Administrator
1. Right-click `WindowsAgent.UI.exe`
2. Select "Run as Administrator"

### 3. Install Service
1. Click **"Install Service"** button in UI
2. Approve UAC prompt
3. Wait for "Service installed successfully" message

### 4. Configure Settings
**Agent Settings Tab:**
- Enter **Agent ID** (from EzgiAI dashboard)
- Enter **Organization ID** (from EzgiAI dashboard)
- Enter **Relay Server URL** (e.g., `wss://relay.ezgiai.com/agent`)
- Enter **API Key (JWT Token)** (from EzgiAI dashboard)

**Database Profiles Tab:**
- Click **"+ Add Database"**
- Select database type (mssql/postgres)
- Enter connection string
- Set limits (timeout, max rows, max concurrent)

### 5. Save Configuration
Click **"Save Configuration"** button

### 6. Start Service
Click **"Start Service"** button

### 7. Verify Connection
Check that:
- 🟢 **Windows Service** shows "Running"
- 🟢 **Relay Connection** shows "Connected to relay server"

## ⚙️ Service Management

### Start Service
```powershell
# Via UI
Click "Start Service" button

# Via Command Line
sc start "EzgiAI Windows Agent"
```

### Stop Service
```powershell
# Via UI
Click "Stop Service" button

# Via Command Line
sc stop "EzgiAI Windows Agent"
```

### Uninstall Service
```powershell
# Via UI
1. Click "Stop Service" (if running)
2. Click "Uninstall" button

# Via Command Line
sc stop "EzgiAI Windows Agent"
sc delete "EzgiAI Windows Agent"
```

## 📝 Configuration File Location

Configuration can be placed in two locations (ProgramData takes priority):

1. **Default**: `C:\Program Files\EzgiAI\agent\appsettings.json`
2. **Override**: `C:\ProgramData\EzgiAI\WindowsAgent\appsettings.json`

## 🔍 Logs

Service logs are written to:
```
C:\ProgramData\EzgiAI\WindowsAgent\logs\agent-YYYYMMDD.json
```

## 🆘 Troubleshooting

### Service won't start
- Check Windows Event Viewer for errors
- Verify config file is valid JSON
- Ensure database connection strings are correct

### UI shows "Service is not installed"
- Run UI as Administrator
- Click "Install Service" button

### Connection to relay server fails
- Verify Relay URL is correct
- Check firewall allows outbound HTTPS (port 443)
- Verify API Key is valid

## 📞 Support

For issues or questions, contact EzgiAI support.
