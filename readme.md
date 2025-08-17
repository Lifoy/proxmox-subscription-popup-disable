# Proxmox Subscription Popup disable from ui

If you have no subscription and visit the webinterface it will popup a no-subscription message  and you get warnings .  
This  will disable this popup .

It Tested and works for: 
* Proxmox Virtual Environment short PVE 9.0.5 on Debian 13 (Trixie)



Before:
![image](https://i.gyazo.com/b46d2f48ad09ec4abea82351656dbab0.png)

After:

![image](https://i.gyazo.com/d1f290da3173343613bd4b437dc415e2.png)



1. Install:
Go To 
```bash
cd /usr/share/javascript/proxmox-widget-toolkit/
```
2. Make a Backup
```bash
cp proxmoxlib.js proxmoxlib.js.bak
```
 OR Re Install the deb Package if needed when you messed up 
 ```bash
apt install --reinstall proxmox-widget-toolkit
```
3. Then open the proxmoxlib.js at line 602 and Replace 
 ```bash
        checked_command: function (orig_cmd) {
        Proxmox.Utils.API2Request({
                url: '/nodes/localhost/subscription',
                method: 'GET',
                failure: function (response, opts) {
                    Ext.Msg.alert(gettext('Error'), response.htmlStatus);
                },
                success: function (response, opts) {
                    let res = response.result;
                    if (
                        res === null ||
                        res === undefined ||
                        !res ||
                        res.data.status.toLowerCase() !== 'active'
                    ) {
                        Ext.Msg.show({
                            title: gettext('No valid subscription'),
                            icon: Ext.Msg.WARNING,
                            message: Proxmox.Utils.getNoSubKeyHtml(res.data.url),
                            buttons: Ext.Msg.OK,
                            callback: function (btn) {
                                if (btn !== 'ok') {
                                    return;
                                }
                                orig_cmd();
                            },
                        });
                    } else {
                        orig_cmd();
                    }
                },
            });
        },
 ```

With this Code 
```bash
        checked_command: function (orig_cmd) {
            Proxmox.Utils.API2Request({
                url: '/nodes/localhost/subscription',
                method: 'GET',
                failure: function (response, opts) {
                    Ext.Msg.alert(gettext('Error'), response.htmlStatus);
                },
                success: function (response, opts) {
                        orig_cmd();
                },
            });
        },
```


4. Restart pveproxy.service and clear browser Cache
```bash
systemctl restart pveproxy.service
```
5. Done
You Have made it :)


⚠️ Important Note About Updates

After updating Proxmox VE, the file:

```bash
/usr/share/javascript/proxmox-widget-toolkit/proxmoxlib.js
```

May be overwritten by the update. This can cause the "No valid subscription" popup to reappear.

If this happens, you will need to reapply the changes described in this guide. 



