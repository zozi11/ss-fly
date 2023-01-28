从一个纯净的centOS服务器，搭建SSR节点

第一步
yum -y install git

第二步
git clone -b master https://github.com/zozi11/ss-fly

第三步（第一个提示是设置一个SSR相关的密码，输入并记住，其它看不懂的可以一路回车）
ss-fly/ss-fly.sh -ssr

一路回车下的默认配置：
password=teddysun.com 
port=11540
stream cipher=aes-256-cfb
protocol=origin
obfs=plain



等待安装结束，出现类似提示：

Your Server IP : 你的服务器ip
Your Server Port : 你的端口
Your Password : 你的密码
Your Protocol : 你的协议
Your obfs : 你的混淆
Your Encryption Method : your_encryption_method

按照这个数据，在软件里新增shadowsockes服务器节点即可使用


到这一步其实就可用了，不过还可以继续开启BBR加速。

第四步，开启BBR加速
ss-fly/ss-fly.sh -bbr
装完后需要重启系统，输入y即可立即重启，或者之后输入reboot命令重启。

判断BBR加速有没有开启成功。

判断命令：

sysctl net.ipv4.tcp_available_congestion_control
返回值为：

net.ipv4.tcp_available_congestion_control = bbr cubic reno
后面有bbr，则说明已经开启成功了。
