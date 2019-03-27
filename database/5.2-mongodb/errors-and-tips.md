# Errors & Tips

## 1. Error: "Address already in use"

输入`mongod`出现无法启动的情况，根据报错可知是"Address already in use"

![](../../.gitbook/assets/image%20%282%29.png)

于是我们输入指令查看系统进程：

```bash
sudo lsof -iTCP -sTCP:LISTEN -n -P
```

![](../../.gitbook/assets/image%20%2813%29.png)

果不其然在最后一行发现正在运行的mongod进程占用了27017这个PID，于是我们需要将其删除：

```bash
sudo kill -9 55147
```

之后再次输入`mongod`则成功运行

