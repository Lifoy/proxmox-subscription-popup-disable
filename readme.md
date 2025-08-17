# Proxmox Subscription Popup disable from ui

If you have no subscription and visit the webinterface it will popup a no-subscription message  and you get warnings .  
This Script will disable this popup .

It works for: 
* Proxmox Virtual Environment short PVE  
  PVE 9

Before:
![image](https://i.gyazo.com/b46d2f48ad09ec4abea82351656dbab0.png)

After:

![image](https://i.gyazo.com/d1f290da3173343613bd4b437dc415e2.png)

Install:
```bash
# get apt script

# for Browser
apt install --reinstall proxmox-widget-toolkit
