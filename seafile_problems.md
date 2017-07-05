- 安装教程
```
http://manual-cn.seafile.com/deploy/using_mysql.html
```

- 问题：安装过程会遇到
```
Failed to connect to mysql server using user "root" and password "***";Acess denied for user 'root'@'loacalhost'
```
输入什么都跳不过去
- 解决方案
出现上述问题，是因为没以root用户运行脚本，使用root用户或sudo运行setup-seafile-mysql.sh脚本即可