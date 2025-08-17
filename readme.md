# Proxmox remove no-subscription message from ui

If you have no subscription and visit the webinterface it will popup a no-subscription message  and you get warnings .  
This Script will disable this popup .

It works for: 
* Proxmox Virtual Environment short PVE  
  PVE 9

Before:
![image]()

After:

![image]()

Install:
```bash
# get apt script

# for Browser
apt install --reinstall proxmox-widget-toolkit
