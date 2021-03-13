# clash-docker-compose
自用国内中转路由，Clash+V2fly+Frp+MTProxy+Shadowsocks

## 如何用

```
sudo su
cd /root
git clone https://github.com/Totoro625/clash-docker-compose.git
cd clash-docker-compose
docker-compose up
```

## 参数



| docker-compose.yml 端口 | 左侧宿主机:右侧docker内部 | 示例配置说明                                                 |
| ----------------------- | ------------------------- | ------------------------------------------------------------ |
| **clash-out**           |                           |                                                              |
| 42103:32103             | clash 控制面板端口        | [推荐管理面板](http://clash.razord.top/#/settings)，默认配置：`youip`端口`42103`密钥`examplepassword004` |
| 42104:7999              | clash http proxy 端口     | 应用最广泛的http代理，默认配置`exampleuser003 examplepassword003` |
| **v2ray-mtp**           |                           |                                                              |
| 42101:32101             | MTProxy 端口              | telegram中代理，默认配置：`https://t.me/proxy?server=youip&port=42101&secret=00baadf00d15abad1deaa515baadcafe` |
| 42102:32102             | Shadowsocks 端口          | 由于v2fly限制，加密方式仅支持`AES-256-GCM` `AES-128-GCM` `ChaCha20-Poly1305` 或称 `ChaCha20-IETF-Poly1305`。默认加密为`ChaCha20-IETF-Poly1305`密码`examplepassword003`端口`42102` |
| **frp-in**              |                           |                                                              |
| 42100:32100             | frp 监听端口              | 内网机器连接端口，默认密码`examplepassword0001`，内网机器配置`frpc.ini` |
| 42200:32200             | 本地映射端口              | 内网网站端口，`frpc.ini`中端口填docker内监听端口`32200`，实际连接用`42200` |

