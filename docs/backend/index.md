# 后端开发

---

## 1 分类简介

后端开发涉及 API 设计、数据存储、服务器部署和消息通信。这些工具是后端开发者日常交互最频繁的伙伴。

!!! tip ""
    根据场景快速选择：
    - 调试 HTTP API → [Postman](api/postman.md) 或 [Apifox](api/apifox.md)
    - 存储结构化数据 → [PostgreSQL](db/sql_db/postgresql.md) 或 [MySQL](db/sql_db/mysql.md)
    - 缓存与键值存储 → [Redis](db/nosql_db/redis.md)
    - 打包环境并部署 → [Docker](container/docker.md)
    - 配置反向代理和 HTTPS → [Nginx](web_srv/nginx.md) 或 [Caddy](web_srv/caddy.md)
    - 服务间异步通信 → [RabbitMQ](mq/rabbitmq.md) 或 [Kafka](mq/kafka.md)

---

## 2 为什么需要这些工具

| 场景 | 痛点 | 解决工具 |
|------|------|---------|
| 开发和测试 API | 没有界面、难以构造请求和断言 | API 客户端可视化构造请求、生成文档、自动化测试 |
| 管理数据库 | 命令行查询结果不直观、难以对比 | 数据库客户端提供查询编辑器 + 可视化执行计划 |
| 环境依赖复杂 | 部署一台新机器需要手动配 JDK/Node/库 | 容器化工具将环境和代码绑定为镜像 |
| 部署 Web 服务 | 需要反向代理、SSL、负载均衡 | Web 服务器配置动静分离、自动证书、流量分发 |
| 微服务间通信 | 同步 HTTP 耦合度太高 | 消息队列解耦、削峰填谷、异步处理 |

---

## 3 子分类速览

### 3.1 API 调试客户端

HTTP 接口的调试、测试与文档生成工具，后端开发的日常主力。

| 工具 | 一句话 |
|------|--------|
| Postman | 最流行的 API 客户端，环境变量 + 集合测试 |
| Insomnia | 轻量 GraphQL 友好的 API 客户端 |
| Apifox | 国产 API 全生命周期管理，文档 + 测试 + Mock 一体 |
| Curl / HTTPie | 终端下的 HTTP 请求命令行工具 |

> [进入 API 调试客户端分类](api/index.md)

### 3.2 关系型数据库

使用 SQL 的结构化数据库，适合事务性强、关系复杂的业务场景。

| 工具 | 一句话 |
|------|--------|
| MySQL | 全球使用最广的开源关系型数据库 |
| PostgreSQL | 功能最丰富的开源数据库，JSON / GIS / 全文搜索都支持 |
| SQLite | 嵌入式数据库，零配置，单文件存储 |

> [进入关系型数据库分类](db/sql_db/index.md)

### 3.3 NoSQL 数据库

非关系型数据存储，适合缓存、搜索、日志等场景。

| 工具 | 一句话 |
|------|--------|
| MongoDB | 文档数据库，支持灵活 Schema，适合快速迭代 |
| Redis | 内存级键值缓存，也支持持久化和消息队列 |
| Elasticsearch | 全文搜索引擎，日志分析和数据检索首选 |

> [进入 NoSQL 数据库分类](db/nosql_db/index.md)

### 3.4 容器化

将应用代码和环境打包为标准镜像，一次构建到处运行。

| 工具 | 一句话 |
|------|--------|
| Docker | 容器化事实标准，镜像构建和运行时 |
| Docker Compose | 定义多容器应用编排的声明式工具 |
| Podman | 无守护进程的 Docker 替代，Rootless 更安全 |

> [进入容器化分类](container/index.md)

### 3.5 Web 服务器

HTTP 服务端软件，提供反向代理、负载均衡和静态资源服务。

| 工具 | 一句话 |
|------|--------|
| Nginx | 反向代理 + 静态资源服务器，性能第一 |
| Apache HTTPD | 老牌 Web 服务器，.htaccess 配置灵活 |
| Caddy | 自动 HTTPS 的反向代理，配置最简洁 |

> [进入 Web 服务器分类](web_srv/index.md)

### 3.6 消息队列

异步通信中间件，解耦微服务之间的同步调用。

| 工具 | 一句话 |
|------|--------|
| RabbitMQ | AMQP 协议的轻量消息队列，适合业务消息 |
| Kafka | 高吞吐分布式消息系统，适合日志流和事件驱动 |

> [进入消息队列分类](mq/index.md)

---

> [回到工具首页](../index.md)
