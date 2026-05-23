[![license](https://img.shields.io/badge/license-Apache--2.0-green.svg)](http://www.apache.org/licenses/LICENSE-2.0)

## 简介

SaaS 短链接系统，基于 JDK17 + SpringBoot3 + SpringCloud 微服务架构，支持高并发、海量存储场景下的短链接生成与跳转。

### 短链接原理

1. **生成唯一标识符**：当用户提交长 URL 时，系统生成唯一的短码
2. **关联存储**：将短码与长 URL 映射关系持久化存储
3. **生成短链接**：短码拼接服务域名，构成短链接
4. **重定向**：访问短链接时，根据短码查找长 URL 并 302 重定向
5. **统计追踪**：记录访问量、来源、设备、地理位置等信息

## 技术栈

- **后端**: JDK17、SpringBoot3、SpringCloud、SpringCloud Alibaba
- **数据库**: MySQL8 + ShardingSphere 分库分表
- **缓存**: Redis + 布隆过滤器
- **消息队列**: RocketMQ
- **服务治理**: Nacos、Sentinel
- **前端**: Vue3 + Vite + Element Plus

## 模块结构

```
shortlink-learning
├── admin          # 管理端服务 - 用户、分组、短链接 CRUD
├── aggregation    # 聚合服务 - 对外 API 聚合层
├── gateway        # 网关服务 - 短链接跳转入口
├── project        # 核心服务 - 短链接生成、跳转、统计
├── console-vue    # 前端控制台
└── resources      # 数据库初始化脚本
```

## 快速开始

### 环境要求

- JDK 17+
- MySQL 8.0+
- Redis 6.0+
- RocketMQ 4.9+
- Nacos 2.x
- Node.js 18+

### 本地运行

1. 初始化数据库：执行 `resources/database/link.sql`
2. 启动 Nacos、Redis、RocketMQ
3. 依次启动 `gateway`、`admin`、`project`、`aggregation` 服务
4. 前端启动：
```bash
cd console-vue
pnpm install
pnpm dev
```

## License

[Apache License 2.0](LICENSE)
