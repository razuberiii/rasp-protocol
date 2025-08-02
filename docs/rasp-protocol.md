# RASP 协议设计文档

## 1. 概述

RASP（Resilient Autonomous Syndication Protocol）是一个去中心化的内容联合发布协议，设计目标是将内容控制权交还给用户，避免中心化服务器带来的风险。

## 2. 核心组件

- **子节点（Subnode）**  
  自由上传内容，管理资源目录，维护推荐节点列表。
- **聚合器（Aggregator）**  
  用户端应用，支持添加子节点，抓取和展示资源。
- **打分系统（Rating System）**（可选）  
  用户可选择参与，记录和上传评分数据。

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

聚合器展示资源并支持点赞、评分等功能

用户可启用打分系统，数据上传到指定仓库

## 5. 法律风险提示
协议仅定义标准，不存储或管理内容。各节点由运营者自行负责内容合规。聚合器仅读取公开信息。