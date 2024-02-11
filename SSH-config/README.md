# Template for $HOME\.ssh\config

\\Change to your (sub)domain\\
Host ssh.example.com
  \\Write this exactly as I have it, not substitutions\\
  ProxyCommand cloudflared access ssh hostname %h
  #Optional \\Specify what user you want to connect with, so you do not need to manually type it every time you make a connection
  User joesmith
  #Optional \\Specify what private key file you want to use so you don't need to type a password either
  IdentityFile C:\Users\joesmith\.ssh\id_rsa
