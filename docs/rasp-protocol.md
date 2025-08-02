# RASP 协议设计文档

## 1. 概述

RASP（Resilient Autonomous Syndication Protocol），旨在让每个用户都能轻松搭建自己的子节点（Node），上传和分享内容，同时通过子节点间的推荐形成分布式内容网络。客户端通过输入一个或多个可信节点地址，访问并浏览整个内容网络。

## 2. 核心组件

- **子节点（Subnode）**  
  自由上传内容，管理资源目录，维护推荐节点列表。
- **聚合器（Aggregator）**  
  客户端应用，支持添加子节点，抓取和展示资源。

## 3. 数据结构

### 3.1 metadata.json 示例

```json
{
  "node_id": "node123#a1b2c3",
  "resources": [
    {
      "id": "video001",
      "title": "示例视频",
      "type": "video",
      "url": "/resources/video001.mp4",
      "hash": "abcdef123456...",
      "support": {
        "wallet": "bc1qxyz...",
        "email": "support@example.com"
      }
    }
  ]
}
```

### 3.2 peering.json 示例
```json
{
  "recommended_nodes": [
    "https://nodeA.example.com",
    "https://nodeB.example.com"
  ]
}
```

## 4. 工作流程
子节点上传资源，生成 metadata.json 和 peering.json

聚合器用户添加子节点地址，抓取资源信息

---

# LICENSE

MIT License