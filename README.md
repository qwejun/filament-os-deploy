# Filament OS

3D打印耗材管理系统

## 快速开始

### 1. 安装 Docker 和 Docker Compose

请先安装 [Docker Desktop](https://www.docker.com/products/docker-desktop)

### 2. 克隆或下载部署文件

```bash
git clone https://github.com/你的用户名/filament-os-deploy.git
cd filament-os-deploy
```

或者直接下载 docker-compose.yml 文件

### 3. 配置环境变量

```bash
# 复制配置示例
cp .env.example .env

# 编辑 .env 文件，设置管理员密码
# ADMIN_USER=admin
# ADMIN_PASS=YourSecurePassword123
```

### 4. 启动服务

```bash
docker-compose up -d
```

### 5. 访问系统

打开浏览器访问：http://localhost:2233

默认管理员账号：
- 用户名：`admin`（或你设置的）
- 密码：`ChangeMe123`（或你设置的）

## 功能特性

- 📦 耗材库存管理
- 🖨️ 打印机状态监控
- 🔄 自动扣减耗材
- 📊 库存统计图表
- 📱 移动端适配
- 🔔 Webhook 通知集成

## 配置说明

### 端口映射

默认使用 `2233` 端口，如需修改请编辑 `docker-compose.yml`：

```yaml
ports:
  - "8080:2233"  # 改为 8080
```

### 数据持久化

- `./data` - 数据库文件
- `./backups` - 备份文件
- `./uploads` - 上传文件

这些目录会被持久化到宿主机。

### 环境变量

| 变量 | 默认值 | 说明 |
|-----|-------|------|
| ADMIN_USER | admin | 管理员用户名 |
| ADMIN_PASS | ChangeMe123 | 管理员密码 |
| DATABASE_URL | file:/app/data/database.sqlite | 数据库路径 |

## 更新镜像

```bash
# 拉取最新镜像
docker-compose pull

# 重启服务
docker-compose up -d
```

## 停止服务

```bash
docker-compose down
```

## 技术栈

- Nuxt 3
- Prisma
- SQLite
- Docker

## License

MIT
