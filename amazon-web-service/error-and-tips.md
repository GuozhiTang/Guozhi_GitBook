# Error & Tips

## 1. Error: PHP is not running

理论上来说安装了apache和php以后两者应该自动配置好相关信息

在CentOS中，Apache的名称叫httpd

apache的配置文件路径是 /etc/httpd/conf/httpd.conf, 找到&lt;Directory /var/www/html&gt;部分，更改AllowOverride从None到All

apache的默认目录是 /var/www/html

安装php具体版本

首先检查当前版本

```bash
php -v
```

查看安装的php扩展包

```bash
yum installed | grep php
```

为了避免冲突，直接删除所有低版本php

```bash
yum remove php*
```

安装epel+website这两个源来安装

CentOS 7.X

```bash
rpm -Uvh https://mirror.webtatic.com/yum/el7/epel-release.rpm
rpm -Uvh https://mirror.webtatic.com/yum/el7/webtatic-release.rpm
```

安装完后使用yum repolist查看已经安装的源

然后比如想安装php5.6和对应的php包

```bash
yum install php56w
yum install php56w-php
yum install php56w-mysql
```

PHP的安装目录在/etc/php.d，配置文件是/etc/php.ini

如果依旧出现错误，则重启httpd试试

```bash
systemctl restart httpd.service     #重启apache
```

重启后测试php

```bash
echo "<?php phpinfo(); ?>"> /var/www/html/index.php
```

然后访问http://"Specific IP"/index.php

