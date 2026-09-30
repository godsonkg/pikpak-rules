# pikpak-rules

自己用的 PikPak 分流规则，Surge / Loon / Clash 通用的文本规则格式。

原来用的是 `whatshub.top/rule/PikPak.list`，里面是迅雷 `sandai.net` 的 CDN 加 `DOMAIN-KEYWORD,mypikpak`，整份都走 DIRECT。问题是 PikPak 限制大陆 IP，App、登录和 API 直连用不了。所以拆成两份：

- `Direct.list`：迅雷 `sandai.net` 的 P2P 加速 CDN，在本规则中走直连；实际速度取决于网络
- `Proxy.list`：PikPak 的 App、账号和 API 域名，要走代理。域名对照了 v2fly/domain-list-community 和 blackmatrix7/ios_rule_script 两份社区列表

## 用法

Surge：

```
RULE-SET,https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Direct.list,DIRECT
RULE-SET,https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Proxy.list,Proxy
```

Loon：

```
https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Direct.list, policy=DIRECT, tag=PikPak-Direct, enabled=true
https://raw.githubusercontent.com/godsonkg/pikpak-rules/main/Proxy.list, policy=Proxy, tag=PikPak-Proxy, enabled=true
```

`Proxy` 换成你配置里的代理策略组名。
