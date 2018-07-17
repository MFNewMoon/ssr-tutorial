# Linux下Shadowsocks设置方法

使用最新的Python版本或是Shadowsocks-libev

### 1.安装：

Python：[https](https://github.com/shadowsocks/shadowsocks/tree/master#install)：[//github.com/shadowsocks/shadowsocks/tree/master\#install](https://github.com/shadowsocks/shadowsocks/tree/master#install)  
Shadowsocks-libev：[https](https://github.com/shadowsocks/shadowsocks-libev#installation)：[//github.com/shadowsocks/shadowsocks-libev\#installation](https://github.com/shadowsocks/shadowsocks-libev#installation)

下面我们以[Python版](https://pypi.python.org/pypi/shadowsocks)的Shadowsocks为例

### 2.设置Shadowsocks配置文件

一个创建³³`/etc/shadowsocks.json`文件，格式如下

```
{

    "server":"服務器IP或域名",

    "server_port":端口號,

    "local_address": "127.0.0.1",

    "local_port":1080,

    "password":"密碼",

    "timeout":300,

    "method":"aes-256-cfb",

    "fast_open": false

}
```

### 3，启动Shadowsocks

Python版客户端命令是sslocal，Shadowsocks-libev客户端命令为ss-local

```
/usr/local/bin/sslocal -c /etc/shadowsocks.json -d start

```

### 4，安装代理链

这里以Debian / Ubuntu为例

```
sudo apt-get install proxychains

```

编辑`/etc/proxychains.conf`

修改最后一行为

```
socks5 127.0.0.1 1080

```

接着我们就可以直接用

```
sudo proxychains apt-get xxxx

sudo proxychains wget xxxx
```

类似的命令使用Shadowsocks进行操作程序

### 5，在应用程序内代理

您只需要将程序指定为**socks v5**的代理

服务器127.0.0.1端口1080（应与Shadowsocks客户端的本地端口对应，默认为1080）

### 6，关闭Shadowsocks

在终端输入

```
lsof –i:1080

```

杀相应pid即可

