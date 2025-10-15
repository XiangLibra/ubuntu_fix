# Google 遠端桌面黑畫面解決方法

儲存，然後重啟 gdm3：
```bash
sudo systemctl restart gdm3
```

確保有安裝與啟用 DBus 與 X server
有些桌面程式、終端機像 gnome-terminal、xfce4-terminal 等都需要有 DBus session bus。
所以確保你安裝了 dbus-x11、xorg 等套件。
在 Debian / Ubuntu 上可能是：

```bash
sudo apt install xfce4 dbus-x11 xorg
```


重啟 Chrome Remote Desktop 服務
進 SSH 或直接連上遠端後跑：
```bash
sudo systemctl restart chrome-remote-desktop@$USER
```



## 設定完後固定的方法

解決方法

先建立群組

```bash
sudo groupadd chrome-remote-desktop
```

把目前使用者加入群組
```bash
sudo usermod -a -G chrome-remote-desktop $USER
```

確認是否加入成功
登出再登入（或重開機），然後執行：
```bash
groups
```

看看輸出裡面有沒有 chrome-remote-desktop。



#磁碟壞掉而變成emengecy mode 終端模式的解決方法

 
```bash
fcsk -yf /dev/sda1
```
然後重開就好

```bash
reboot
```
