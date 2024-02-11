# Windows Service (best but more complicated)

This option is the best for automation, it runs seamlessly in the background with no popups or anything. Almost too well, because if you want to see logs you have to actually open the logfile and such rather than have a terminal window open with all of the STDOUT. I digress.  

In PowerShell or other shell, you would want to navigate to the folder you put the cloudflared executable in, and then use the following command. This installs the base service. If you follow the folder structure to a Tee, then it will work, but pay very special attention to the pathing. You must ensure you copy the cert.pem file to the `Systemprofile\.cloudflared` folder that is created when you run the first command, not the `.cloudflared` folder we have been working with so far in your $HOME directory.  

Note: if you already have set it up via the normal guide, then you will only need to copy the cert.pem and .json files we already have over to this new folder.

`cloudflared.exe service install`  
`mkdir C:\Windows\System32\config\systemprofile\.cloudflared`  
Then run...  and authenticate via link.
`cloudflared.exe login`
`copy C:\Users\%USERNAME%\.cloudflared\cert.pem C:\Windows\System32\config\systemprofile\.cloudflared\cert.pem`  
`cloudflared.exe tunnel create <Tunnel Name>`  

Then you will receive a new .json file with your tunnel ID as the title in your user profile, at this point copy it over.  
`copy C:\Users\%USERNAME%\.cloudflared\<Tunnel-ID>.json C:\Windows\System32\config\systemprofile\.cloudflared\<Tunnel-ID>.json`  

Copy over your config.yml file into this folder, or create a new one using the template I provided. 

Now, it's registry time. Go to..  
`Computer\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Cloudflared`  

Now you edit the `ImagePath` registry entry with where your exe and config file is, and I discovered you can also set other options like you would on the command line here as well.  

`C:\Cloudflared\bin\cloudflared.exe --config=C:\Users\%USERNAME%\.cloudflared\config.yml tunnel run`  
Now if the service doesn't automatically start, you can navigate to the exe folder and run this...  

`sc start cloudflared`  

If you change your config file options, you can run `sc stop cloudflared` and then run the start command again, or simply open the "Services" app, then right click on the cloudflared service and click restart.  


# Task Scheduler Method (easier, but not as good)

In order to have this run automatically and not create a service, what you want to do is create a new task in Task Scheduler, to start when "On logon" (if you have your PC set to automatically log in, which I assume most would if they want their services available when they're away from home). If you don't have your PC setup to login automatically then I would use "On Startup". You might need to play around with what user it uses, I used the "Administrators" service account, but I have seen Local Service work, as well as your user, whatever fits your security profile. 
