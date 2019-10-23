# Error & Tips

## 1. Error: PHP is not running

理论上来说安装了apache和php以后两者应该自动配置好相关信息

如果依旧出现错误，则重启httpd试试

```bash
systemctl restart httpd.service     #重启apache
```

