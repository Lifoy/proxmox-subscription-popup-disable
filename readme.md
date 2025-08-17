# Proxmox remove no-subscription message from ui

If you have no subscription and visit the webinterface it will popup a no-subscription message  and you get warnings .  
This Script will disable this popup .

It works for: 
* Proxmox Virtual Environment short PVE  
  PVE 9

Before:
![image](https://github.com/thethink3r/Proxmox-remove-no-subscription-message/assets/132231658/fa89042f-11a1-48d8-89da-37d86237db5f)

After:

![image](https://github.com/thethink3r/Proxmox-remove-no-subscription-message/assets/132231658/a8235b40-4b65-4731-b2fa-3aeb2cd91563)

Install:
```bash
# get apt script
wget -O /etc/apt/apt.conf.d/pve-no-subscription-message https://raw.githubusercontent.com/thethink3r/Proxmox-remove-no-subscription-message/main/pve-no-subscription-message

# for Browser
apt install --reinstall proxmox-widget-toolkit
