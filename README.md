# Filament OS Go 版本 - NAS 部署指南

## 快速开始

```bash
# 1. 进入部署目录
cd filament-os-deploy

# 2. 创建环境变量配置文件
cp .env.example .env
# 编辑 .env 文件，设置你自己的管理员账号密码

# 3. 创建数据目录
mkdir -p data recordings bambu-streams backups logs

# 4. 启动服务
docker compose up -d

# 5. 查看日志
docker logs -f filament-os-go
```

## 访问地址

- 本地: http://localhost:2233
- NAS: http://你的NAS-IP:2233

## 账号配置

**首次启动前必须设置管理员账号！**

编辑 `.env` 文件：

```bash
INIT_ADMIN_USERNAME=你的用户名
INIT_ADMIN_PASSWORD=你的密码
```

如果不设置，服务会启动但**不会创建管理员账号**，你将无法登录。

## 环境变量说明

| 变量名 | 必填 | 默认值 | 说明 |
|--------|:--:|:------:|------|
| `INIT_ADMIN_USERNAME` | ✅ | - | 初始管理员用户名 |
| `INIT_ADMIN_PASSWORD` | ✅ | - | 初始管理员密码 |
| `PORT` | ❌ | `2233` | 服务端口 |
| `JWT_SECRET` | ❌ | 自动生成 | JWT密钥 |

## 数据持久化

所有数据保存在当前目录的子文件夹中：

```
./data           # SQLite 数据库、会话文件
./backups        # FTP 备份文件
./bambu-streams  # 视频流缓存
./recordings     # 录像文件
./logs           # 日志文件
```

## 注意事项

1. **账号安全**: 首次启动时从环境变量读取账号密码创建管理员
2. **修改账号**: 如需修改已有账号，请登录后在系统设置中修改
3. **忘记密码**: 删除 `data/filament-os.db` 重新启动（会丢失所有数据）
