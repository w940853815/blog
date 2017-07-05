1 添加root用户密码
sudo passwd

2 设置root用户可ssh登录
- vi /etc/ssh/sshd_config
- 找到

```
PermitRootLogin without-password
```

- 改为
```
PermitRootLogin yes
```
- 重启ssh
'''
service ssh restart
'''
