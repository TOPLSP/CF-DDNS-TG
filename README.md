
自动更新 DNS 解析 到本机 IP 地址，支持 ipv4 和 ipv6 以 本地（内网）IP 和 公网 IP。(适合共享主机)


创建 Cloudflare API 令牌，请转到 https://dash.cloudflare.com/profile/api-tokens 并按照以下步骤操作：
1. 单击创建令牌
2. 为令牌提供一个名称，例如，`cloudflare-ddns`
3. 授予令牌以下权限：
    * 区域 - 区域 - 读取
    * 区域 - 区域设置 - 读取
    * 区域 - DNS - 编辑
4. 将区域资源设置为：
    * 包括 - 特定区域 - 选择你想设置的域名
5.或者直接给账号APIkey
#下载脚本
```
# curl -sS -O https://raw.githubusercontent.com/TOPLSP/CF-DDNS-TG/main/cf-ddns.sh && chmod +x cf-ddns.sh
```
root目录下面找到 cf-ddns.sh 并配置相关参数:
 * CFKEY=api密钥，访问: https://www.cloudflare.com/a/account/my-account 获取
 * CFUSER=登录邮箱
 * CFZONE_NAME=域名
 * CFRECORD_NAME=主机名
 * CFRECORD_TYPE=A   A=ipv4/AAAA=ipv6
 * CFTTL=20           20-120
 * FORCE=false       true=强制更新ip

TGbot设置
 * API_TOKEN=""   @botfather 获取 bot token
 * CHAT_ID=""     @userinfoid 获取 userID
发送内容
 * MESSAGE="[xxx]IP已更新为 $WAN_IP"    xxx为主机

```

# crontab -e
# */2 * * * * cf-ddns.sh >/dev/null 2>&1
# or you need log:
# */2 * * * * /cf-ddns.sh >> /var/log/cf-ddns.log 2>&1

```

用法:
cf-ddns.sh -k cloudflare-api-key \
* -u user@example.com \
* -h host.example.com \     # fqdn of the record you want to update
* -z example.com \          # will show you all zones if forgot, but you need this
* -t A|AAAA                 # specify ipv4/ipv6, default: ipv4
* -f false|true \           # force dns update, disregard local stored ip



基于   修改


