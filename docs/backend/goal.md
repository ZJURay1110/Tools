# backend — 后端开发

## 定位

收录后端开发与运维工具，涵盖 API 调试客户端、数据库管理与客户端、容器化、Web 服务器、消息队列。

## 子分类目录结构

```
backend/
├── api/                      # API 调试客户端
│   ├── postman.md
│   ├── insomnia.md
│   ├── apifox.md
│   └── curl_httpie.md
├── db/                       # 数据库
│   ├── sql_db/               #   关系型数据库
│   │   ├── mysql.md
│   │   ├── postgresql.md
│   │   └── sqlite.md
│   └── nosql_db/             #   非关系型数据库
│       ├── mongodb.md
│       ├── redis.md
│       └── elasticsearch.md
├── container/                # 容器化
│   ├── docker.md
│   ├── docker_compose.md
│   └── podman.md
├── web_srv/                  # Web 服务器
│   ├── nginx.md
│   ├── apache_httpd.md
│   └── caddy.md
└── mq/                       # 消息队列
    ├── rabbitmq.md
    └── kafka.md
```

## 编写要点

- API 客户端对比 GraphQL/gRPC/REST 支持与自动化测试能力
- 数据库工具说明连接管理、查询编辑器、可视化执行计划
- Web 服务器侧重反向代理、负载均衡、静态资源、HTTPS 配置
