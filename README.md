![Ninetail-Fox Memory Logo](docs/assets/logo-render.png)

# 🦊 Ninetail-Fox Memory
**The AI Memory Exoskeleton for Indie Hackers**

为 Cursor、Claude Desktop 等多代理打造的 100% 本地化、隐私绝对安全的“单兵记忆外骨骼”。
抛弃昂贵的云端 API，将你的核心上下文安全地锁在本地 SQLite 中。

---

## 📸 界面预览

![Ninetail-Fox Memory Pro UI](docs/assets/ui-screenshot.png)

---

## 💡 为什么需要 Ninetail-Fox？

在大模型并发时代，上下文（Context）就是生产力。
*   **100% 本地隐私**：你的代码和灵感不应成为大模型的免费训练语料。所有记忆存储于本地 SQLite。
*   **多代理共享**：在 Cursor 写代码，去 Claude 查逻辑，记忆实时无缝漫游。
*   **极速响应**：基于 SQLite 的底层优化，拒绝云端向量数据库的网络延迟。

---

## 🛠️ 技术透视：Under the Hood

Ninetail-Fox 构建于复杂的混合检索与量化风控之上。下图展示了我们的核心记忆调度引擎：从多供应商嵌入 (embedding_provider) 到混合检索引擎 (HybridSearchEngine)，再到事实抽取 (FactExtractor) 的无缝协同。

![System Topology](docs/assets/topology.png)

> [!NOTE]
> 架构核心：Bi-Encoder (语义粗筛) + BM25 (关键词补充) + Cross-Encoder (精排重测) + Time Decay (时间衰减)。

---

## 👑 Ninetail-Fox V4.5 Pro 版专属特性

开源版提供了基础的记忆框架，但如果你需要投入真正的实战开发，**V4.5 Pro** 提供了企业级的性能压缩与风控管理：

| 特性 | 开源版本 (OS) | Pro 版本 (V4.5) |
| :--- | :--- | :--- |
| **量化压缩** | 基础存储 | **Google TurboQuant (Int8)** 压缩 19.8x |
| **内存占用** | 随记忆增加 | **极低常驻** (优化 LRU 淘汰机制) |
| **噪音过滤** | 简单关键词 | **LittleFox 独家风控算法** (思维剪枝) |
| **系统架构** | Python 源码 | **全平台原生预编译包** (Win/Mac/Linux) |
| **备份恢复** | 手动 | **一键急救重置 & 自动化云备份脚本** |

> [!IMPORTANT]
> **TurboQuant (Int8) 技术**：在 1536 维向量检索中，由于标量量化的引入，我们将内存碎片化率降低了 80%，实现了在极低内存占用下支持“无限”对话记忆。

---

## 🚀 如何获取 Pro 版？(早鸟特惠进行中)

Pro 版代码库目前为私有状态，采用一次性买断制，无需承担持续的 Token 订阅费。

*   **日常买断价**：~~¥99~~
*   **🔥 前 100 名盲筹早鸟价**：**¥59** (含 V5.0 免费升级资格)

### 购买方式：

1.  **扫码支付**：扫描下方微信赞赏码完成支付。

![WeChat Pay](docs/assets/wechat-pay.png)

2.  **添加微信**：扫描下方二维码添加开发者微信，备注“**Ninetail Pro**”，并发送支付截图。

![WeChat Contact](docs/assets/wechat-contact.png)

3.  **获取分发**：审核后，我将直接发送对应操作系统的免配置安装包，并拉你进入 **Pro 用户专属社群**。

---

## 🚀 快速开始 (开源版)

如果你希望先尝试开源版本，请按照以下步骤操作：

```bash
# 克隆仓库
git clone https://github.com/sunhonghua1/ninetails-memory-engine.git

# 安装依赖
pip install -r requirements.txt

# 启动 MCP Server
python engine/mcp_memory_server.py
```

---

Ninetail-Fox Memory Pro v4.5 · Built for the future of AI Agents · © 2026
