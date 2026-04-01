# 🎉 FilamentOS - 3D 打印智能管家

> **不只是耗材管理，更是你的 3D 打印智能管家**
>
> 从入库到打印完成，全程自动化管理，让 3D 打印变得更简单、更智能、更高效

---

## ✨ 为什么选择 FilamentOS？

| 💡 痛点 | 🚀 FilamentOS 解决方案 |
|--------|------------------------|
| 耗材太多，记不清库存 | AI 智能识别 + 扫码入库，3 秒完成登记 |
| 打印到一半发现耗材不够 | 实时库存监控，打印前自动预警 |
| 多卷耗材混用，追踪困难 | AMS 槽位绑定，每卷耗材都有"身份证" |
| 打印完成忘记扣库存 | 自动扣料系统，打印结束自动更新库存 |
| 多打印机管理混乱 | 统一仪表盘，所有打印机状态一目了然 |
| 成本核算麻烦 | AI 智能报价，打印前就知道成本 |

---

## 🚀 快速开始

### 1. 安装 Docker 和 Docker Compose

请先安装 [Docker Desktop](https://www.docker.com/products/docker-desktop)

### 2. 克隆部署仓库

```bash
git clone https://github.com/qwejun/filament-os.git
cd filament-os/filament-os-deploy
```

### 3. 配置环境变量

```bash
# 复制配置示例
cp .env.example .env

# 编辑 .env 文件，设置管理员密码
# INIT_ADMIN_USERNAME=admin
# INIT_ADMIN_PASSWORD=YourSecurePassword123
```

### 4. 启动服务

```bash
docker-compose up -d
```

### 5. 访问系统

打开浏览器访问：http://localhost:2233

默认管理员账号：
- 用户名：`admin`（或你设置的）
- 密码：`ChangeMe_123456`（或你设置的）

---

## 📦 核心功能

### 🤖 AI 视觉识别入库（行业首创）

对着耗材标签拍张照，系统自动识别：
- ✅ 品牌 Logo（拓竹、eSun、Polymaker 等 50+ 品牌）
- ✅ 材质类型（PLA、PETG、ABS、TPU、ASA、PC 等）
- ✅ 颜色名称 + 色号（如"11100 象牙白"）
- ✅ 重量规格（1kg、500g、250g）

**批量入库模式**：一次拍摄最多支持 10 卷耗材同时识别，入库效率提升 10 倍！

---

### 🖨️ 打印机智能管家

**实时状态仪表盘**

```
🟢 X1C (在线)
   ├─ 任务: 机械齿轮 v3.stl
   ├─ 进度: ████████████░░ 78%
   ├─ 剩余: 45 分钟
   ├─ 温度: 喷嘴 215°C | 热床 60°C
   └─ AMS: [PLA白] [PLA蓝] [空] [空]

🟡 P1S (暂停)
🔴 A1 mini (离线)
```

**支持的打印机型号**
- ✅ Bambu Lab X1C / X1E / P1P / P1S / A1 / A1 mini / H2D / H2S

---

### 🎯 AMS 智能槽位管理 + 扣料记录

**可视化 AMS 面板**

```
┌───┐ ┌───┐ ┌───┐ ┌───┐
│A1 │ │A2 │ │A3 │ │A4 │  ← AMS 单元 1
│🟦 │ │🟥 │ │⬜ │ │⬛ │
└───┘ └───┘ └───┘ └───┘
绑定    绑定   空    空
#2401  #2402
```

**一键槽位绑定** → **自动扣料追踪** → **扣料流水记录** → **多色打印支持**

每次扣料都会记录：时间、打印机、槽位、用量、剩余重量，支持手动校正

---

### 💬 AI 智能助手

**自然语言库存查询**

| 你的问题 | AI 回答 |
|---------|---------|
| "我有多少卷 PLA？" | "你有 12 卷 PLA，其中 8 卷已开封，剩余总重量约 6.8kg" |
| "蓝色耗材还剩多少？" | "找到 3 卷蓝色耗材：拓竹 PLA 蓝（剩 450g）、eSun PETG 天蓝（剩 800g）..." |
| "打印这个 150g 模型要多少钱？" | "预估成本 ¥25.00（耗材 ¥18 + 机器折旧 ¥7）" |

**视觉识别黑科技**
- 上传 Bambu Studio 截图
- AI 自动识别切片参数
- 智能成本估算

---

### 📊 数据洞察

**可视化仪表盘**
- 📈 耗材使用趋势
- 🥧 品牌偏好分析
- 🎨 材质占比统计
- 🔥 热门颜色矩阵

---

### 🔔 智能通知

**支持的通知渠道**
- 💬 企业微信
- 📱 钉钉
- 💜 Discord
- 🏠 Home Assistant
- 🔗 自定义 Webhook

**触发事件**：打印完成、库存不足、打印失败等

---

### 📱 移动端体验

- 📷 相机直接拍照入库
- 👆 触摸优化
- 🔔 推送通知
- 📲 PWA 安装（像原生 App 一样使用）

---

## 🛠️ 系统要求

| 资源 | 最低要求 | 推荐配置 |
|------|---------|---------|
| CPU | 2 核 | 4 核 |
| 内存 | 2GB | 4GB |
| 存储 | 5GB | 20GB+ |
| 网络 | 局域网 | 公网访问 |

---

## 🔧 常用命令

```bash
# 查看日志
docker-compose logs -f

# 停止服务
docker-compose down

# 重启服务
docker-compose restart

# 更新镜像
docker-compose pull
docker-compose up -d
```

---

## 🗂️ 数据持久化

以下目录会被持久化到宿主机：

- `./data` - 数据库文件
- `./backups` - 备份文件
- `./uploads` - 上传文件

---

## 🛡️ 安全特性

- 🔑 JWT Token 认证
- 🔒 bcrypt 密码加密
- ⏰ 7 天免登录
- 🚫 登录速率限制
- 💾 本地数据存储（完全私有化）

---

## 🤝 开源社区

**GitHub**: https://github.com/qwejun/filament-os

**问题反馈**: https://github.com/qwejun/filament-os/issues

**详细功能文档**: 见 [FEATURES.md](https://github.com/qwejun/filament-os/blob/main/FEATURES.md)

---

## 📄 许可证

MIT License - 自由使用、修改、分发

---

**Made with ❤️ by 3D 打印爱好者，为 3D 打印爱好者**

*FilamentOS - 让耗材管理变得简单、智能、高效*
