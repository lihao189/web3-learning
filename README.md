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
第 1 周（Day 1–7） — 环境与 Solidity 入门
Day 1：安装开发环境

安装 Node.js、npm/yarn、Git、VSCode。注册 GitHub 并建一个 repo（web3-learning）。

交付物：GitHub repo 初始化（README + .gitignore）。

Day 2：安装并熟悉 Hardhat

npm init + npm install --save-dev hardhat，创建第一个 Hardhat 项目（sample project）。

运行 sample tests。

交付物：Hardhat 项目 commit。

Day 3：读 Solidity 基础（变量、函数、mapping、事件）

阅读并做笔记（Solidity 基础章节），完成一个简单 Storage 合约（存/取 uint）。

交付物：Storage.sol + 单元测试（Hardhat）。

Day 4：CryptoZombies 或等效交互式课程第一章

跟着做至少一章练习（变量/函数/事件理解）。

交付物：练习截图/小结写进 README。

Day 5：编写第一个可部署合约 & 本地 deploy

使用 Hardhat 在本地网络（Hardhat Network）部署 Storage，并写一个简单脚本调用它。

交付物：部署脚本与运行记录（console 输出）。

Day 6（周末）：Foundry 入门（可选但强烈推荐）

安装 Foundry（forge/anvil），运行示例项目，比较 Foundry、Hardhat 的差异。

交付物：Foundry 环境 setup 指南写入 repo。

Day 7（周末）：复盘 + 小练习日

回顾本周内容，整理笔记，把 Storage 完善测试（包括边界测试）。

交付物：周总结（README 更新）。

第 2 周（Day 8–14） — Solidity 进阶与测试
Day 8：Solidity 常用类型与控制结构（struct、enum、modifier）

编写含 struct 的小合约（例如简单投票/白名单结构）。

交付物：合约 + 单测。

Day 9：事件与日志、gas 模型理解

在合约中加入事件并在测试中监听。写说明：哪些操作更耗 gas。

交付物：gas 实验结果（README）。

Day 10：错误处理与异常（require, revert, assert）

改写合约以包含 require 检查，写测试覆盖异常路径。

交付物：异常测试用例。

Day 11：部署脚本与环境管理（.env、网络配置）

配置 Hardhat 对接本地与 testnet（准备好 Alchemy/Infura key，但暂不充值）。

交付物：.env.example + deploy 脚本样板。

Day 12：开始写 ERC20（理解标准接口）

用 OpenZeppelin 的 ERC20 模板写一个简单代币合约（继承实现）。

交付物：MyToken.sol。

Day 13（周末）：完成 ERC20 测试与交互脚本

写 transfer/approve 边界与权限测试，写 mint/空投脚本在本地网络跑通。

交付物：测试覆盖报告（简单统计）。

Day 14（周末）：写 Week2 总结 & 把 repo 整理成样板项目

写好 README，列出下一周目标（NFT 与前端）。

交付物：整理后的 repo（可供复制的样板）。

第 3 周（Day 15–21） — NFT（ERC721）与 IPFS
Day 15：了解 ERC721 与 metadata 结构

阅读 ERC721 标准，做一个简单 NFT 合约模板。

交付物：MyNFT.sol 草稿。

Day 16：实现并测试 ERC721（mint, transfer）

使用 OpenZeppelin ERC721，写 mint 流程与安全检查。

交付物：测试用例。

Day 17：理解并实践 IPFS 基础（存储 metadata）

学习如何把 JSON metadata 上传到 IPFS（可以尝试本地 ipfs 或公共 pinning）。

交付物：示例 metadata.json + ipfs CID。

Day 18：前端基础（React + ethers.js）入门

初始化 React 项目，安装 ethers.js，能在页面上连接 MetaMask（wallet connect 可选）。

交付物：简单页面能读取地址。

Day 19：把前端与 NFT 合约连通（铸造按钮）

实现铸造（mint）按钮，调用合约 mint，前端显示交易 hash。

交付物：可交互的铸造页面截图或 GIF。

Day 20（周末）：部署 NFT 到本地 testnet（anvil 或 Hardhat node）并完整测试

把前端、后端（可选）一起跑通，模拟用户铸造与查看 NFT。

交付物：完整 demo（录屏或 README 步骤）。

Day 21（周末）：写 NFT 项目 README & 抛出已知问题列表

列出遇到的问题、待改进项（gas 优化、metadata 扩展）。

交付物：项目文档。

第 4 周（Day 22–28） — 开始接触后端（Java + web3j）与事件监听
Day 22：熟悉 web3j（Java 库）基础

新建 Maven/Gradle 项目，添加 web3j 依赖，写能连本地节点的示例（查询区块号）。

交付物：Java demo：getBlockNumber。

Day 23：用 web3j 读取合约 ABI 与 events

生成合约 Java wrapper（web3j 工具），监听 ERC20/ERC721 的 Transfer 事件。

交付物：事件监听 demo 程序。

Day 24：把事件写入数据库（SQLite 或 PostgreSQL）

简单实现事件入库模板（schema：txHash, blockNumber, from, to, tokenId）。

交付物：事件入库脚本 + sample rows。

Day 25：实现重试、幂等与断点续跑策略

在 Java 服务中加入幂等检查（txHash 唯一约束）与断点续跑逻辑。

交付物：服务设计文档 + 代码片段。

Day 26：集成 HTTP API（用 Spring Boot）

写一个简单的 REST 接口返回最新事件 / token 持有者信息。

交付物：Spring Boot 项目 skeleton & 示例 endpoint。

Day 27（周末）：完整部署事件监听服务到本地并结合合约（端到端）

从合约向后端发事件，后端入库并通过 API 返回。

交付物：端到端 demo（README 步骤 + logs）。

Day 28（周末）：复盘 Java 后端部分并写成设计文档

把异常处理、重试策略、资源限制写成文档，准备加入 CI。

交付物：设计文档 commit。

第 5 周（Day 29–35） — 安全基础、工具链扩展与测试增强
Day 29：学习常见合约漏洞（重入、整数溢出、delegatecall 问题）

阅读漏洞说明，写漏洞示例合约并在本地演示攻击（实践最佳学习法）。

交付物：漏洞示例代码 + 防护改写。

Day 30：引入静态分析工具（Slither）并跑你的合约

安装 Slither，运行在你的 ERC20/ERC721 项目上，修复简单问题。

交付物：Slither 报告截图 + 已修复问题 commit。

Day 31：学习并使用 OpenZeppelin Contracts 与 AccessControl

用 OZ 的 AccessControl / Ownable 改写权限逻辑并测试。

交付物：合约权限升级后的版本。

Day 32：写更多单元测试 & 边界条件（包括模拟恶意调用）

用 Hardhat/Foundry 写一套更严格的测试（包括 fail-case）。

交付物：测试覆盖率说明（至少列出关键场景）。

Day 33：介绍审计流程与写简单审计清单（Checklist）

列出审计要点并在 repo 中新增 AUDIT.md。

交付物：AUDIT.md。

Day 34（周末）：实践：把项目做成 CI 流程（GitHub Actions）

写基本 CI：lint、run tests、run slither（如果可行）。

交付物：.github/workflows/ci.yml。

Day 35（周末）：复盘并整合所有安全修复（写 changelog）

把所有已处理的安全问题汇总成 changelog。

交付物：CHANGELOG.md。

第 6 周（Day 36–42） — 进阶：部署到 Testnet、前端完善、钱包 UX
Day 36：准备并连通测试网（Sepolia/Goerli 视情况）

配置 Hardhat network （Alchemy/Infura key），检查 gas 与账户。

交付物：.env.example 更新（包含说明）。

Day 37：把 ERC20/ERC721 部署到 Testnet（小金额）

部署合约并记录地址与 tx hash。

交付物：部署记录（tx link / 地址）。

Day 38：前端 UX 改进：交易状态、确认数、错误处理

在前端显示交易确认进度、错误信息和 gas 预估。

交付物：前端改进 PR。

Day 39：集成 WalletConnect / web3modal（多钱包支持）

支持 MetaMask 之外的连接方式（手机钱包也能用）。

交付物：支持多钱包的 demo 页面。

Day 40：添加后端签名或转发（谨慎）示例（仅做演示）

演示如何在后端构造交易并让客户端签名（注意安全警示）。

交付物：示例代码 + 安全警告文档。

Day 41（周末）：做 E2E 测试：从前端发起交易到后端入库再到前端展示

完整录制流程并写成操作文档。

交付物：E2E 文档 + 录屏。

Day 42（周末）：把项目部署说明写成「一键上手」指南

包含：如何运行本地 node、部署合约、启动后端、启动前端。

交付物：GETTING_STARTED.md。

第 7 周（Day 43–49） — 深入工具：Foundry、The Graph、链上索引
Day 43：用 Foundry 写 Solidity 单元测试（forge）

把至少一个合约的测试用例迁移或重写为 forge 测试。

交付物：forge tests。

Day 44：学习 The Graph 基础概念（subgraph）

阅读 The Graph 文档并准备 subgraph scaffold（schema + mappings）。

交付物：subgraph scaffold。

Day 45：实现一个简单的 subgraph（索引 Transfer 事件）

在本地 or 测试网索引你的合约事件并能查询。

交付物：subgraph 已运行的截图/查询示例。

Day 46：集成前端使用 subgraph 查询数据（取代 RPC 轮询）

前端调用 GraphQL，展示 token 列表或交易历史。

交付物：前端查询功能上线。

Day 47：研究 Layer2（概念）与常见选择（Optimism/Arbitrum）

写一页笔记：为什么要用 L2，迁移成本有哪些。

交付物：Layer2 调研笔记。

Day 48（周末）：实现一个小功能：把一个查询或报表交给 The Graph 提供给前端

例如：按 holder 排序的 NFT 列表或最近交易榜。

交付物：Graph + 前端展示。

Day 49（周末）：复盘工具链（Foundry/Graph），写工具对比与选择建议

交付物：工具对比文档（便于未来项目选型）。

第 8 周（Day 50–56） — 进阶专题：可升级合约、多签、治理、形式化验证
Day 50：学习合约可升级方案（Proxy pattern / OZ Upgrades）

写一个简单的可升级合约 demo（代理 + 实现合约）。

交付物：Upgradable demo。

Day 51：实现并测试多签钱包（简化版或导入现成实现）

测试多签流程（提案 -> 投票 -> 执行）。

交付物：多签合约 + 测试。

Day 52：DAO 治理基础（治理代币、投票机制）

写一份小设计：如何为你的项目设计治理流程。

交付物：治理设计文档。

Day 53：形式化验证与额外工具简介（Certora / K-framework 仅入门）

阅读简介并尝试简单示例（可选）。

交付物：形式化验证笔记。

Day 54：跨链/桥接概念与风险（研究）

写一页说明：桥的攻击面是什么，是否要用桥。

交付物：跨链风险评估文档。

Day 55（周末）：把高级特性（可升级、多签、治理）整合到 demo 项目中一部分

例如：把多签作为管理员入口并演示升级流程。

交付物：集成 demo。

Day 56（周末）：做一次安全复审（用 slither + 手动检查）并把未解决问题列出

交付物：安全复审清单与修复计划。

第 9 周（Day 57–60） — 项目收尾、作品集、求职准备
Day 57：整理并清理 repo（文档、注释、LICENSE）

确保每个模块都有 README、部署与运行步骤。

交付物：整洁的 repo（可用于展示）。

Day 58：准备演示材料（项目简介 PPT / Demo 视频 3–5 分钟）

录制一段 demo（铸造 NFT -> 后端入库 -> 前端显示全过程）。

交付物：Demo 视频 + PPT 大纲。

Day 59：写技术博客 / 项目说明（1 篇 1000–1500 字）

把学习过程、关键技术点、安全注意点写成博文（可发到简书/掘金/GitHub Pages）。

交付物：技术博客草稿或已发布链接。

Day 60：求职/转型准备：简历 + 面试题目清单 + 下一步计划

把你的项目写入简历（项目描述、关键技术、你解决的挑战），列出常见面试题（Solidity、安全、系统设计）并写复习计划。

交付物：更新后的简历（含项目链接）与 30 天后进一步学习计划。

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


