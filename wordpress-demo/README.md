# WordPress 博客演示项目

这是一个使用 Docker 搭建的 WordPress 博客演示项目。本项目包含了完整的 WordPress 环境，包括 WordPress 核心和 MySQL 数据库。

## 环境要求

- Docker
- Docker Compose

## 快速开始

1. 克隆本项目到本地

2. 在项目目录中运行：
   ```bash
   docker-compose up -d
   ```

3. 等待容器启动完成后，访问：
   http://localhost:8000

4. 按照 WordPress 安装向导完成初始化设置

## 配置信息

- WordPress 访问地址：http://localhost:8000
- 数据库用户名：wordpress
- 数据库密码：wordpress
- 数据库名：wordpress

## 目录结构

- `docker-compose.yml`: Docker 编排配置文件
- `wordpress_data/`: WordPress 文件目录（自动创建）
- `db_data/`: MySQL 数据目录（自动创建）

## 停止服务

```bash
docker-compose down
```

## 数据持久化

所有数据都通过 Docker volumes 持久化存储，重启容器不会丢失数据。