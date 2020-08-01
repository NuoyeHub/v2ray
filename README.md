# v2ray
最好用的 V2Ray 一键安装脚本 &amp; 管理脚本

这里收集一下本人网站所撰写的文章，因为域名老是被墙，换来换去的，现在直接在 WIKI 备份一下，不怕看不到了。

# 资助 V2Ray
请考虑 [资助 V2Ray](https://www.v2ray.com/chapter_00/02_donate.html) 发展。

# 温馨提示
我们的永久域名是：233v2.com (已墙)

此 WIKI 仅作备份使用，内容可能无法与网站保持同步。

# V2Ray 一键安装脚本
[V2Ray 一键安装脚本](https://github.com/233boy/v2ray/wiki/V2Ray%E4%B8%80%E9%94%AE%E5%AE%89%E8%A3%85%E8%84%9A%E6%9C%AC)

# V2Ray 搭建教程
这是为小白而准备 V2Ray 搭建教程，详细的图文教程确保你可以百分百成功搭建 V2Ray 使用。

[V2Ray搭建详细图文教程](https://github.com/233boy/v2ray/wiki/V2Ray%E6%90%AD%E5%BB%BA%E8%AF%A6%E7%BB%86%E5%9B%BE%E6%96%87%E6%95%99%E7%A8%8B)

# V2Ray客户端使用教程
Windows
[V2RayN使用教程](https://github.com/233boy/v2ray/wiki/V2RayN%E4%BD%BF%E7%94%A8%E6%95%99%E7%A8%8B)


# Cloudflare 中转
担心 IP 被墙？或者不想 IP 被墙？是的！使用 Cloudflare 来中转 V2Ray 的 WebSocket 流量就行！

[使用Cloudflare中转V2Ray流量](https://github.com/233boy/v2ray/wiki/%E4%BD%BF%E7%94%A8Cloudflare%E4%B8%AD%E8%BD%ACV2Ray%E6%B5%81%E9%87%8F)

# 安装
要求：Ubuntu 16+ / Debian 8+ / CentOS 7+  
推荐系统荐使用 Debian 9 系统，脚本会自动启用 BBR 优化。  
备注：不推荐使用 Debian 8 系统，因为 Caddy 申请证书可能会出现一些莫名其妙的问题   

使用 root 用户输入下面命令安装或卸载 

```
bash <(curl -s -L https://git.io/v2ray.sh)
```

> 
>如果提示 curl: command not found ，那是因为你的 VPS 没装 Curl  
>ubuntu/debian 系统安装 Curl 方法: ``apt-get update -y && apt-get install curl -y``  
>centos 系统安装 Curl 方法: ``yum update -y && yum install curl -y `` 
>安装好 curl 之后就能安装脚本了  

备注：安装完成后，输入``v2ray`` 即可管理 V2Ray  
如果提示你的系统不支持此脚本，那么请尝试更换系统  

# 快速管理
``v2ray info`` 查看 V2Ray 配置信息  
``v2ray config`` 修改 V2Ray 配置  
``v2ray link`` 生成 V2Ray 配置文件链接  
``v2ray infolink`` 生成 V2Ray 配置信息链接  
``v2ray qr`` 生成 V2Ray 配置二维码链接  
``v2ray ss`` 修改 Shadowsocks 配置  
``v2ray ssinfo`` 查看 Shadowsocks 配置信息  
``v2ray ssqr`` 生成 Shadowsocks 配置二维码链接  
``v2ray status`` 查看 V2Ray 运行状态  
``v2ray start`` 启动 V2Ray  
``v2ray stop`` 停止 V2Ray  
``v2ray restart`` 重启 V2Ray  
``v2ray log`` 查看 V2Ray 运行日志  
``v2ray update`` 更新 V2Ray  
``v2ray update.sh`` 更新 V2Ray 管理脚本  
``v2ray uninstall`` 卸载 V2Ray  

# 配置文件路径
V2Ray 配置文件路径：/etc/v2ray/config.json  
Caddy 配置文件路径：/etc/caddy/Caddyfile  
脚本配置文件路径: /etc/v2ray/233blog_v2ray_backup.conf  

>
>警告，请不要修改脚本配置文件，免得出错。。  
>如果你不是有特别的需求，也不要修改 V2Ray 配置文件  
>不过也没事，若你实在想要瞎折腾，出错了的话，你就卸载，然后重装，再出错 ，再卸载，再重装，重复到自己不再想折腾为止。。  
>

# WS+TLS / HTTP2
如果你使用了这两个协议，那么就会使用了脚本自带的 Caddy 集成  
不管如何，不建议直接去更改 Caddy 的配置：/etc/caddy/Caddyfile  
如果你需要配置其他网站相关，请将网站的配置文件放到 /etc/caddy/sites 目录下，然后重启 Caddy 进程即可，脚本默认生成的 Caddy 的配置会加载 /etc/caddy/sites 这个目录下的所有配置文件。  
所以，请将你的网站配置文件放到 /etc/caddy/sites 目录下，完完全全不需要去更改 /etc/caddy/Caddyfile  
记得重启 Caddy 进程：service caddy restart  

# Caddy 插件相关  
本脚本集成了 Caddy，但不集成任何 Caddy 插件，如果你需要安装某些 Caddy 插件，你可以使用官方的 Caddy 安装脚本来一键安装。  
本人的脚本集成的 Caddy 的安装路径，跟 Caddy 官方的安装脚本是一致的。所以可以直接安装，不会有任何问题  
举个例子，安装包含 http.filebrowser 插件的 Caddy，执行如下命令即可  

```
curl https://getcaddy.com | bash -s personal http.filebrowser
```

你可以在 https://caddyserver.com/download 找到 Caddy 更多插件和安装命令。  

# 备注
V2Ray 客户端配置文件 SOCKS 监听端口为 2333， HTTP 监听端口为 6666  
可能某些 V2Ray 客户端的选项或描述略有不同，但事实上，此脚本显示的 V2Ray 配置信息已经足够详细，由于客户端的不同，请对号入座。  

# 备份安装方法
确保你已经 Fork 了脚本，将 233boy 修改成你的 Github 用户名  

```
git clone https://github.com/nuoyehub/v2ray -b master
cd v2ray
chmod +x install.sh
./install.sh local
```
