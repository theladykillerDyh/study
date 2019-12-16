# linux study

## echo

将一个文件的内容清空，向一个文件输入空。

```shell
echo >/home/logs/trip-mall.log
```

## tail

实时查看日志文件的尾内容。

```shell
tail -f /home/logs/tirp-mall.log
```

## 查看系统中运行的端口号

```shell
ps -ef|grep 8080
```

或

```shell
nestate -ano|grep 8080
```

## 根据PID杀进程

```shell
kill -9 pid
```

## 通过telnet协议访问服务器端口号

*Telnet协议*是TCP/IP*协议*族中的一员，通过telnet命令测试某个端口是否关闭打开

```shell
telnet ip port
```

## 磁盘操作

```
df -hT
```

<img src="C:\Users\86173\AppData\Roaming\Typora\typora-user-images\image-20191213164855422.png" alt="image-20191213164855422" style="zoom: 50%;" />

```shell
mount -t drvfs F: /mnt/f
```

```shell
#给某个用户重新密码
passwd username
```

