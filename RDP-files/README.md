Enter this command into Powershell, Command Prompt, Terminal, etc. Or better yet, put this command into a .ps1 file and run directly in PowerShell. 

#### LEAVE LOCALHOST AS LOCALHOST!

```PowerShell
cloudflared access rdp --hostname rdp.example.com --url rdp://localhost:3390
```

SUBSTITUTE your sub/domain for rdp.example.com, but LEAVE LOCALHOST AS LOCALHOST!

Put port to whatever port (unused) you want. It does NOT correspond to the port that RDP is running
on the target device. In fact, if you use 3389, it will probably fail as it's already in use by 
the client device's default RDP. So choose a random port, the cloudflare tunnel itself will route 
to the correct port on the target machine, as that is what the config.yml defines
