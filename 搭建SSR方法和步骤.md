





购买 VPS 的步骤我就不说了。

这里主要记录下主要的步骤，方便下次需要搭建随时可以查阅。



（1）在购买的 VPS 中创建好服务，添加 SSH（这是为了能方便连接VPS ）。

1. 连接方法一：打开 Git Bash：`ssh root@ip`，默认端口为 22，另外这里的 ip 地址为你的 VPS 地址
2. 连接方法二：或者使用 Xshell、Putty 等工具也可以连接



（2）连接上后，依次输入如下命令来安装：

``` xml
yum -y install wget  # 这个命令为了来安装 wget

#这个命令为：安装 ssr 注意：这个脚本可能没用
wget -N --no-check-certificate https://softs.fun/Bash/ssr.sh && chmod +x ssr.sh && bash ssr.sh
```

> 注意：如果上面那个脚本没用的话使用下面这个脚本试试：
>
> ``` xml
> wget -N --no-check-certificate https://raw.githubusercontent.com/ToyoDAdoubi/doubi/master/ssr.sh && chmod +x ssr.sh && bash ssr.sh
> ```



（3）然后会出现一个界面，按照意思安装和配置即可，这样就完成了搭建。



（4）但是你还可以进行 BBR 加速（什么是 BBR：[*SSR开启Google的BBR内核脚本加速TCP（附BBR一键安装脚本）*](https://www.moidea.info/archives/445.html)）

> 此加速为谷歌 `BBR` 加速，`Vultr` 的服务器框架可以装 `BBR` 加速，加速后对速度的提升很明显，所以推荐部署加速脚本，该加速方法是开机自动启动，部署一次就可以了。

依次输入下面命令：

``` xml
yum -y install wget

wget --no-check-certificate https://github.com/teddysun/across/raw/master/bbr.sh

chmod +x bbr.sh

./bbr.sh
```

注意：不动的时候按回车，然后耐心等待，最后重启 VPS 服务器即可。重启命令：`reboot`

如果前面那个 BBR 加速失败，出现问题，那么看下该文这个：[BBR+BBR魔改+Lotsever(锐速)一键脚本 for Centos/Debian/Ubuntu](https://github.com/XX-net/XX-Net/issues/6506)

``` xml
支持系统：Centos 6+/Debian 8+/Ubuntu 14+

加速脚本安装，先运行如下命令：

wget -N --no-check-certificate "https://raw.githubusercontent.com/chiakge/Linux-NetSpeed/master/tcp.sh" && chmod +x tcp.sh && ./tcp.sh
```



（5）最后，判判断是否开启 BBR 加速，比如输入命令：`lsmod|grep bbr`，如果出现 tcp_bbr 字样表示bbr已安装并启动成功。



（6）下载相应的 SSR 客户端填写对应信息就可以了。

配置完以后就可以使用 `SSR` 客户端来尝试是否能访问 [Google](https://link.juejin.im?target=https%3A%2F%2Fwww.google.com)，还有一点要注意如果要用 `SS` 客户端的话，上面配置中的 `协议` 必须为 `origin` ，混淆必须为 `plain` ，这样就可以使用 `SS` 客户端了（即 `协议` 和 `混淆` 可以不填）。

- `Mac` 版 `SSR` 客户端 [下载地址](https://link.juejin.im?target=https%3A%2F%2Fgithub.com%2Fshadowsocksr-backup%2FShadowsocksX-NG%2Freleases)、[备用下载地址](https://link.juejin.im?target=https%3A%2F%2Fnofile.io%2Ff%2FjgMWFwCBonU%23ab0d3c3b6ac54482)。
- `Windows` 版 `SSR` 客户端 [下载地址](https://link.juejin.im?target=https%3A%2F%2Fgithub.com%2Fshadowsocksr-backup%2Fshadowsocksr-csharp%2Freleases)、[备用下载地址](https://link.juejin.im?target=https%3A%2F%2Fnofile.io%2Ff%2F6Jm7WJCyOVv%2FShadowsocksR-4.7.0-win.7z)。
- `Android` 版 `SSR` 客户端 [下载地址](https://link.juejin.im?target=https%3A%2F%2Fgithub.com%2Fshadowsocksr-backup%2Fshadowsocksr-android%2Freleases%2Fdownload%2F3.4.0.8%2Fshadowsocksr-release.apk)、[备用下载地址](https://link.juejin.im?target=https%3A%2F%2Fnofile.io%2Ff%2FrvTJoj0h5GC%2Fshadowsocksr-release.apk)。
- `iOS` 版 `SSR` 客户端：`Potatso Lite`、`Potatso`、`shadowrocket` 都可以作为 `SSR` 客户端，但这些软件目前已经在国内的 `App Store` 下架，可以用美区的 `AppID` 账号来下载，国内的话可以用 `SuperWingy`，但这是 `SS` 客户端，不支持 `SSR`。



参考：[使用 Vultr 搭建 SSR 服务器的方法 - 掘金](<https://juejin.im/post/5bbdbffcf265da0ac2568a80>)