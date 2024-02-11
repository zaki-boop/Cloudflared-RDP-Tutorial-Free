# Template for $HOME\.ssh\config

`Host ssh.example.com`  
&nbsp;&nbsp;&nbsp;&nbsp; `ProxyCommand cloudflared access ssh hostname %h`  
&nbsp;&nbsp;&nbsp;&nbsp; `User joesmith`  
&nbsp;&nbsp;&nbsp;&nbsp; `IdentityFile C:\Users\joesmith\.ssh\id_rsa`


--  Change to your (sub)domain --  
`Host ssh.example.com`  
&nbsp;&nbsp;&nbsp;&nbsp; -- Leave this exactly the same --  
&nbsp;&nbsp;&nbsp;&nbsp; `ProxyCommand cloudflared access ssh hostname %h`  
&nbsp;&nbsp;&nbsp;&nbsp; -- Optional: Specify what user you want to connect with --  
&nbsp;&nbsp;&nbsp;&nbsp;   `User joesmith`  
&nbsp;&nbsp;&nbsp;&nbsp; -- Optional \\Specify what private key file you want to use --  
&nbsp;&nbsp;&nbsp;&nbsp;   `IdentityFile C:\Users\joesmith\.ssh\id_rsa`
