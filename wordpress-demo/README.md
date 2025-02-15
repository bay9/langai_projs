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
- 数据库密码：WP_User@2023#Secure
- 数据库名：wordpress

## 目录结构

- `docker-compose.yml`: Docker 编排配置文件
- `wordpress_data/`: WordPress 文件目录（自动创建）
- `db_data/`: MySQL 数据目录（自动创建）

## 维护指南

### 日常维护

1. 定期备份
   ```bash
   # 备份数据库
   docker exec wordpress-demo_db_1 mysqldump -u wordpress -pWP_User@2023#Secure wordpress > backup.sql
   
   # 备份WordPress文件
   tar -czf wordpress_files.tar.gz wordpress_data/
   ```

2. 更新容器
   ```bash
   docker-compose pull   # 拉取最新镜像
   docker-compose up -d  # 重新启动容器
   ```

### 故障排除

1. 容器无法启动
   - 检查端口占用：`lsof -i :8000`
   - 检查日志：`docker-compose logs`

2. 数据库连接失败
   - 确认数据库容器运行状态：`docker ps`
   - 检查数据库日志：`docker-compose logs db`

3. WordPress访问缓慢
   - 检查系统资源使用情况
   - 考虑启用缓存插件

## 停止服务

```bash
 docker-compose down
```

## 数据持久化

所有数据都通过 Docker volumes 持久化存储，重启容器不会丢失数据。数据存储在以下位置：
- WordPress文件：`./wordpress_data`
- 数据库文件：`./db_data`

建议定期备份这些目录以防数据丢失。