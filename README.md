
自动更新 DNS 解析 到本机 IP 地址，支持 ipv4 和 ipv6 以 本地（内网）IP 和 公网 IP。

创建 Cloudflare API 令牌，请转到 https://dash.cloudflare.com/profile/api-tokens 并按照以下步骤操作：

1. 单击创建令牌
2. 为令牌提供一个名称，例如，`cloudflare-ddns`
3. 授予令牌以下权限：
    * 区域 - 区域 - 读取
    * 区域 - 区域设置 - 读取
    * 区域 - DNS - 编辑
4. 将区域资源设置为：
    * 包括 - 特定区域 - 选择你想设置的域名
```

# curl https://raw.githubusercontent.com/yulewang/cloudflare-api-v4-ddns/master/cf-v4-ddns.sh > /usr/local/bin/cf-ddns.sh && chmod +x /usr/local/bin/cf-ddns.sh
# run `crontab -e` and add next line:
# */2 * * * * /usr/local/bin/cf-ddns.sh >/dev/null 2>&1
# or you need log:
# */2 * * * * /usr/local/bin/cf-ddns.sh >> /var/log/cf-ddns.log 2>&1


# Usage:
# cf-ddns.sh -k cloudflare-api-key \
#            -u user@example.com \
#            -h host.example.com \     # fqdn of the record you want to update
#            -z example.com \          # will show you all zones if forgot, but you need this
#            -t A|AAAA                 # specify ipv4/ipv6, default: ipv4
#            -f false|true \           # force dns update, disregard local stored ip
```

CFKEY=api密钥，请访问: https://www.cloudflare.com/a/account/my-account 获取
CFUSER=登录邮箱
CFZONE_NAME=域名
CFRECORD_NAME=主机名
CFRECORD_TYPE=A   A=ipv4/AAAA=ipv6
CFTTL=1           20-120
FORCE=false       true=强制更新ip

# TGbot设置  @botfather bottoken/@userinfoid
API_TOKEN=""
CHAT_ID=""
# 发送内容
MESSAGE="[xxx]IP已更新为 $WAN_IP"

基于  修改
