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
| 42104:7999              | clash http 端口           | 应用最广泛的http代理，默认配置`exampleuser002 examplepassword002` `exampleuser003 examplepassword003` |
| **v2ray-mtp**           |                           |                                                              |
| 42101:32101             | MTProxy 端口              | [telegram](https://telegram.org/)中代理，默认配置：`https://t.me/proxy?server=youip&port=42101&secret=00baadf00d15abad1deaa515baadcafe` |
| 42102:32102             | Shadowsocks 端口          | 由于v2fly限制，加密方式仅支持`AES-256-GCM` `AES-128-GCM` `ChaCha20-Poly1305` 或称 `ChaCha20-IETF-Poly1305`。默认加密为`ChaCha20-IETF-Poly1305`密码`examplepassword005`端口`42102` |
| **frp-in**              |                           |                                                              |
| 42100:32100             | frp 监听端口              | 内网机器连接端口，默认密码`examplepassword001`，内网机器配置`frpc.ini` |
| 42200:32200             | 本地映射端口              | 内网网站端口，`frpc.ini`中端口填docker内监听端口`32200`，实际连接用`42200` |

## 你应该修改的配置

| 名称             | 密码                                                         |
| ---------------- | ------------------------------------------------------------ |
| Frp 密码         | examplepassword0001                                          |
| Clash 用户1      | exampleuser002                                               |
| Clash 密码1      | examplepassword002                                           |
| Clash 用户2      | exampleuser003                                               |
| Clash 密码2      | examplepassword003                                           |
| Clash 控制密码   | examplepassword004                                           |
| MTProxy 密钥     | 00baadf00d15abad1deaa515baadcafe 随机生成地址`openssl rand -hex 16` |
| Shadowsocks 密码 | examplepassword005                                           |
|                  |                                                              |

## 注意事项

MTProxy仅为第一代，仅供个人学习使用

详见：https://guide.v2fly.org/app/mtproto.html