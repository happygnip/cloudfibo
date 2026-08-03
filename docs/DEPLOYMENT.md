# Docker Compose 部署

本文档用于 CloudFibo 单机体验与小规模部署。正式生产环境应根据资源规模、可用性、备份、安全域和合规要求完成架构评估。

## 部署内容

标准 Compose 包包含 PostgreSQL、Redis、Temporal、Prometheus、Alertmanager、CloudFibo Backend、CloudFibo Web 和统一网关。默认使用本地登录模式，不包含 Keycloak 与 Backstage。

## 前置条件

- 一台 Linux 或 Windows 服务器。
- Docker Engine 与 Docker Compose v2。
- Linux 环境安装 `openssl`；Windows 建议使用 PowerShell 7+。
- 可访问 Release 中声明的容器镜像仓库，或提前准备离线镜像包。
- 对外使用时准备域名和受信任 CA 证书；体验环境可使用脚本生成的自签证书。

具体 CPU、内存、磁盘和操作系统支持范围将在每个 Release 的说明中给出。

## 获取安装包

从仓库的 **Releases** 页面下载与目标版本对应的 Compose 包。发布流水线也会将同一批文件同步到以下阿里云 OSS 公开目录：

```text
https://cloudfibo-release.oss-cn-beijing.aliyuncs.com/compose/<product-version>/<image-tag>/
```

已验证可公开下载的离线镜像包：

[cloudfibo-compose-v3.3.5-build.2026070801.tar](https://cloudfibo-release.oss-cn-beijing.aliyuncs.com/compose/3.3.5/v3.3.5-build.2026070801/cloudfibo-compose-v3.3.5-build.2026070801.tar)

该历史版本只包含离线镜像包与镜像清单；从下一次 Release 开始，流水线会同时发布 Compose 部署目录和 SHA-256 校验文件。不要混用不同版本的部署文件、后端镜像与前端镜像。

每个版本包含：

- `cloudfibo-compose-<image-tag>.tar.gz`：Compose 部署目录。
- `cloudfibo-compose-<image-tag>.tar`：离线镜像包。
- `cloudfibo-compose-<image-tag>-images.txt`：镜像清单。
- `cloudfibo-compose-<image-tag>-SHA256SUMS.txt`：下载文件校验值。

下载后先验证文件完整性：

```bash
sha256sum -c cloudfibo-compose-<image-tag>-SHA256SUMS.txt
```

```bash
tar -xzf cloudfibo-compose-<version>.tar.gz
cd deploy/docker-compose
```

## Linux 部署

```bash
chmod +x ./deploy.sh
./deploy.sh \
  --public-origin "https://cloudfibo.example.com:8443" \
  --gateway-https-port 8443
```

## Windows 部署

```powershell
Set-Location deploy/docker-compose
.\deploy.ps1 `
  -PublicOrigin "https://cloudfibo.example.com:8443" `
  -GatewayHttpsPort 8443
```

脚本将自动生成运行配置、随机数据库与 Redis 凭据、RSA 密钥、本地 HTTPS 证书和告警回调 Token，然后校验 Compose 配置、拉取镜像并启动服务。

## 验证

```bash
docker compose ps
curl -sS http://127.0.0.1:8080/healthz
curl -k -sS https://127.0.0.1:8443/healthz
```

浏览器访问：

```text
https://cloudfibo.example.com:8443/
```

如使用自签证书，浏览器会显示安全提示。正式环境请替换为受信任 CA 签发的证书。

## 申请并导入 License

1. 登录 CloudFibo。
2. 打开“系统管理 → 许可证”。
3. 复制平台指纹。
4. 按 [License 申请说明](LICENSE_REQUEST.md) 通过邮件提交申请。
5. 收到 `.lic` 文件后在许可证页面导入并确认状态为“有效”。

## 运维提示

- 妥善备份 `.env`、后端配置、Redis 配置、网关证书和 Docker 数据卷。
- 不要把运行时密码、私钥、Token 或真实 License 提交到 GitHub。
- 升级前备份 PostgreSQL 和持久化卷，并阅读目标 Release 的升级说明。
- `docker compose down -v` 会删除数据库和监控数据卷，请勿在生产环境随意执行。
- 默认 HTTP 端口仅用于本机健康检查；公网访问应使用 HTTPS。

## 下一步

首个公开 Release 发布后，本页将补充精确下载地址、最低资源配置与升级路径。
