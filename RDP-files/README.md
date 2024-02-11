Enter this command into Powershell, Command Prompt, Terminal, etc. Or better yet, put this command into a .ps1 file and run directly in PowerShell. 

#### LEAVE LOCALHOST AS LOCALHOST!

```PowerShell
cloudflared access rdp --hostname rdp.example.com --url rdp://localhost:3390
```

SUBSTITUTE your sub/domain for rdp.example.com, but LEAVE LOCALHOST AS LOCALHOST!

What is essentially happening is the "cloudflared access ..." part is establishing a connection with the service at the given subdomain you use, and then creating a tunnel between that subdomain (which is pointing at your RDP subdomain) to whatever port you specify on your client machine. Then you connect to  your own port, which tunnels your traffic between endpoints securely. 

Put port to whatever port (unused) you want. It does NOT correspond to the port that RDP is running
on the target device. In fact, if you use 3389, it will probably fail as it's already in use by 
the client device's default RDP. So choose a random port, the cloudflare tunnel itself will route 
to the correct port on the target machine, as that is what the config.yml defines.
