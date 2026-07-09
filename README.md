# pikpak-rules

个人维护的 PikPak 分流规则集，Surge/Loon/Clash 通用格式（classical text list）。

原规则来源 `whatshub.top/rule/PikPak.list`（讯雷 sandai.net CDN + `DOMAIN-KEYWORD,mypikpak`），
但整个规则集在原仓库统一走 DIRECT——这对 PikPak 主 App 是错的：PikPak 对国内 IP 有区域限制，
主 App/账号/API 必须走代理，只有 sandai.net 这个 P2P 加速 CDN 才该走直连。故拆成两个文件：

- `Direct.list` = 讯雷(sandai.net) P2P 加速 CDN，国内可达更快，走直连
- `Proxy.list` = PikPak 主 App/账号/API 域名，交叉合并 v2fly/domain-list-community 与
  blackmatrix7/ios_rule_script 两个社区源（`mypikpak.com`/`.net`、`pikpak.me`/`.io`、
  `pikpakdrive.com`、`pickpackapp.com`），必须走代理才能用

## 用法

Surge:
```
RULE-SET,https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Direct.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Proxy.list,Proxy
```

Loon:
```
https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Direct.list, policy=DIRECT, tag=PikPak-Direct, enabled=true
https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Proxy.list, policy=Proxy, tag=PikPak-Proxy, enabled=true
```
