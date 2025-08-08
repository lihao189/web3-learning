# Web3 学习指南（中文）

> 目标读者：有后端经验的 Java 开发者，想在 60 天内系统掌握以太坊智能合约开发、dApp 全栈和 Java 后端集成技能。

---

## 目录
1. 介绍
2. 学习目标（60 天）
3. 环境与工具
4. 核心学习资料（中文）
5. 视频与课程（中文 / 带中文字幕）
6. 面向 Java 的实战资源（web3j）
7. 实战项目建议（优先级）
8. 安全 / 测试 / CI 工具
9. 如何把成果放到简历与面试材料中
10. 一键起步：仓库结构建议
11. 致谢与后续

---

## 1. 介绍
本 README 面向中文读者，把学习路线、关键中文资源、实战项目和工具链集中到一个文件，方便直接 fork 到你的 `web3-learning` 仓库并作为日常打卡清单使用。

## 2. 学习目标（60 天）
- 熟练使用 Solidity 写合约，理解常见漏洞与防护；
- 熟练使用 Hardhat / Foundry 做本地开发、测试、部署；
- 能用 React + ethers.js 编写基本前端并接入钱包；
- 能用 Java (web3j) 写链上事件监听服务并入库；
- 能把一个小型项目（ERC20/721 + 前端 + 后端监听）部署到测试网并形成展示材料。

## 3. 环境与工具（建议安装）
- Node.js（v16/18+），npm / yarn
- Hardhat（JS/TS 开发环境）或 Foundry（forge/anvil）
- Git & GitHub
- MetaMask（浏览器钱包）
- Java 11+、Maven/Gradle（用于 web3j）
- SQLite/Postgres（事件入库测试）

## 4. 核心学习资料（中文）
> **官方与权威中文文档**（优先收藏）

- Solidity 中文文档（官方翻译/社区镜像）：https://docs.soliditylang.org/zh-cn/latest/index.html
- Hardhat 中文入门（登链社区整理）：https://learnblockchain.cn/article/1356
- Foundry 中文文档（登链社区整理）：https://learnblockchain.cn/docs/foundry/i18n/zh/
- OpenZeppelin 官方文档（英文原站，社区有中文翻译/镜像）：https://docs.openzeppelin.com/
- CryptoZombies 中文互动教程（Solidity 入门）：https://cryptozombies.io/zh/lesson/1

## 5. 视频与课程（中文 / 带字幕）
- B 站搜索关键词（直接可搜）：`Solidity 智能合约 教程`、`Hardhat 教程`、`Foundry 教程`、`以太坊 开发 实战`。
- 常见实战合集（示例）：Patrick Collins 的 Solidity 全套课程（B 站多数有带中文字幕的合集）。

## 6. 面向 Java 的实战资源（web3j）
- web3j 中文教程 / 快速上手文章（示例博客 & 文档集合）：可在掘金 / CSDN / 博客园 搜 `web3j 教程`。
- web3j 官方：在 GitHub 上搜索 `web3j` 并查看使用示例（生成合约 wrapper、事件监听、交易签名）。

## 7. 实战项目建议（逐步实现）
1. ERC20 代币 + 本地测试（mint/transfer/approve）
2. ERC721（NFT）+ IPFS 存储 metadata + 前端铸造页
3. Java 服务：监听 Transfer 事件并写入数据库（SQLite/Postgres）
4. 可升级合约（Proxy）或简化多签/DAO（进阶）

每个项目都写好 README、测试、部署脚本与前端 demo（录屏 3–5 分钟）。

## 8. 安全 / 测试 / CI 工具（中文资料较多）
- Slither（静态分析）
- MythX / 形式化验证（进阶）
- OpenZeppelin Contracts（标准实现，建议优先使用）
- Foundry / forge（高效的 Solidity 测试框架）
- GitHub Actions：自动化运行测试、Slither 检查

## 9. 如何把成果放到简历与面试材料中
- 每个项目写 1–2 段技术要点（你负责的工程难点），列出关键合约地址与 demo 视频链接；
- 强调 Java + web3j 的工程实践（事件监听、幂等性、断点续跑、错误重试策略）；
- 写一篇技术博客或在掘金/简书发布项目解析，便于面试官检索。

## 10. 一键起步：仓库结构建议
```
web3-learning/
├─ contracts/           # Solidity 合约
├─ frontend/            # React + ethers.js
├─ backend/             # Java (web3j) 事件监听服务
├─ scripts/             # Hardhat / Foundry 部署脚本
├─ test/                # 单元测试（JS/forge）
├─ docs/                # 学习笔记、AUDIT.md、GETTING_STARTED.md
└─ README.md
```


