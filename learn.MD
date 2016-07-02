### 编辑service
>测试的
>>先编辑
```
vim /etc/systemd/system/hello.service
sudo systemctl start hello.service
```
查看服务是否已经运行
```
sudo systemctl list-utils hello*
```

设定成为开机运行的服务
```
sudo systemctl enable hello.service
```

查看内核日志
```
journalctl --dmesg
```
查看系统日志，包含了内核日志
```
journalctl --system
```
查看指定的服务日志
```
journalctl --unit hello.service
```
类似tail -f 那样的跟踪日志
```
journalctl --follow
```
指定时间区间
```
journalctl --unit hello.service --since "year-month-day hour:min:sec" --until "year-month-day hour:min:sec"
journalctl --unit hello.service --since today

```
输出格式 改为JSON， 同事将最新的日志放到上面,输出10行
```
journalctl --unit hello.service --lines 10 --output json-pretty --reverse
journalctl /usr/lib/systemd/systemd
```

列出service文件以及状态

```
sudo systemctl list-unit-files hello*
```


```
sudo systemctl enable hello.service
sudo systemctl disable hello.service
```

当修改service后

```
sudo systemctl stop hello.service
sudo systemctl daemon-reload
sudo systemctl start hello.service
```
当删除service后

```
sudo systemctl stop hello.service
sudo systemctl list-units hello*
```
修复后
```
sudo systemctl enable hello.service
sudo systemctl start hello.service
```

彻底清除
```
rm -rf /etc/systemd/system/hello.service
sudo systemctl reset-failed
```

