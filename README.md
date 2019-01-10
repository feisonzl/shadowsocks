# shadowsocks
1.使用方式
```
$sudo ./ss.sh
```

2.开机启动服务配置
方法一：
```
$sudo echo -e 'nohup /usr/local/bin/ssserver -c /etc/shadowsocks.json -d start' >> /etc/rc.local
```
方法二：
```
$sudo vi /etc/systemd/system/shadowsocks-server.service
[Unit]
Description=Shadowsocks Server
After=network.target

[Service]
Type=forking
TimeoutStartSec=0
ExecStart=/usr/local/bin/ssserver -c /etc/shadowsocks.json -d start

[Install]
WantedBy=multi-user.target

$sudo systemctl daemon-reload
$sudo systemctl start shadowsocks-server.service
```
