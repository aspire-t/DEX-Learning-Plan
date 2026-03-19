# DEX 学习清a单（14 天可执行版）

## 使用方式

- 每天投入 1.5\~3 小时，按“读源码/文档 -> 看视频 -> 动手验证 -> 记录结论”执行。
- 每天必须产出 1 个可验证结果：笔记、脚本、测试或最小页面。
- 遇到看不懂的函数，先画调用链，再回到业务语义。

## 阶段目标

- 第 1-4 天：打牢 AMM 与 Uniswap V2 核心模型。
- 第 5-9 天：打通 Router、前端调用与链上交互闭环。
- 第 10-12 天：理解 V3 集中流动性与工程化工具链。
- 第 13-14 天：完成一个最小可运行 DEX 学习项目并复盘。

***

## Day 1：AMM 基础与 x\*y=k

### 学习任务

- 理解恒定乘积做市模型、滑点、价格冲击。
- 写出 3 个交易规模下的价格变化样例。

### 必读资料

- Uniswap V2 Core: <https://github.com/Uniswap/v2-core>
- Uniswap V2 白皮书: <https://uniswap.org/whitepaper.pdf>

### 视频资料

- YouTube - How Uniswap V2 Liquidity Pools Work: <https://www.youtube.com/watch?v=oPvqt7kSwbg>
- Bilibili - Uniswap V2 白皮书讲解: <https://www.bilibili.com/video/BV11L41147VN/>

### 当日产出

- 一页笔记：解释“为什么买得越多越贵”。

***

## Day 2：Uniswap V2 Core 架构总览

### 学习任务

- 区分 Core 与 Periphery 职责边界。
- 阅读 Factory 与 Pair 的关系。

### 必读资料

- v2-core README: <https://github.com/Uniswap/v2-core>
- Uniswap V2 概览文档: <https://docs.uniswap.org/contracts/v2/overview>
- 深入理解 V2 合约（中文）: <https://github.com/adshao/publications/blob/master/uniswap/dive-into-uniswap-v2-contracts/README_zh.md>

### 视频资料

- Bilibili - UniswapV2 智能合约代码解析: <https://www.bilibili.com/video/BV1pg411c7w7/>

### 当日产出

- 一张图：Factory -> Pair 创建与查找流程图。

***

## Day 3：读懂 Pair.swap

### 学习任务

- 重点阅读 `UniswapV2Pair.sol` 的 `swap`。
- 搞清输入输出约束、手续费和 K 不变量检查。

### 必读资料

- Pair 合约: <https://github.com/Uniswap/v2-core/blob/master/contracts/UniswapV2Pair.sol>
- V2 Core 仓库: <https://github.com/Uniswap/v2-core>

### 视频资料

- Bilibili - UniswapV2 智能合约代码解析: <https://www.bilibili.com/video/BV1pg411c7w7/>

### 当日产出

- 一段自己的伪代码：`swap` 执行步骤。

***

## Day 4：读懂 mint / burn 与 LP 份额

### 学习任务

- 阅读 `mint`、`burn`，理解 LP Token 如何代表份额。
- 理解手续费累计对 LP 收益的影响。

### 必读资料

- Pair 合约（mint/burn）: <https://github.com/Uniswap/v2-core/blob/master/contracts/UniswapV2Pair.sol>
- V2 白皮书: <https://uniswap.org/whitepaper.pdf>

### 视频资料

- YouTube - Finematics 频道（DeFi 基础系列）: <https://www.youtube.com/c/Finematics/videos>

### 当日产出

- 一页说明：LP 的进入、退出与收益来源。

***

## Day 5：Router02 与 getAmountsOut

### 学习任务

- 阅读 `UniswapV2Router02.sol` 与 `UniswapV2Library`。
- 理解 `getAmountsOut`、路径与多跳报价。

### 必读资料

- v2-periphery: <https://github.com/Uniswap/v2-periphery>
- Router02 合约: <https://github.com/Uniswap/v2-periphery/blob/master/contracts/UniswapV2Router02.sol>
- Quick Start: <https://docs.uniswap.org/contracts/v2/guides/smart-contract-integration/quick-start>

### 视频资料

- Bilibili - Uniswap V2 前端代码解析 Part 1: <https://www.bilibili.com/video/BV1Uv411N7Ry>

### 当日产出

- 一页笔记：`getAmountsOut` 与真实成交价格为什么可能不同。

***

## Day 6：授权与交易执行链路

### 学习任务

- 理解 `approve -> swapExactTokensForTokens` 的调用链。
- 理解 `amountOutMin`、`deadline` 的保护作用。

### 必读资料

- Router02 合约: <https://github.com/Uniswap/v2-periphery/blob/master/contracts/UniswapV2Router02.sol>
- ERC20 标准: <https://eips.ethereum.org/EIPS/eip-20>

### 视频资料

- YouTube - Uniswap 官方频道: <https://www.youtube.com/@Uniswap>

### 当日产出

- 一页流程图：前端按钮点击到链上交易确认。

***

## Day 7：前端接入基础（viem + wagmi）

### 学习任务

- 钱包连接、读取报价、构造写交易。
- 处理 pending/success/revert 状态。

### 必读资料

- viem: <https://github.com/wevm/viem>
- wagmi: <https://github.com/wevm/wagmi>

### 视频资料

- YouTube - Patrick Collins 智能合约课程: <https://www.youtube.com/watch?v=gyMwXuJrbJQ>

### 当日产出

- 最小前端页面：连接钱包并读取一个链上数据。

***

## Day 8：把报价、授权、交换串起来

### 学习任务

- 完成最小 Swap 页面：输入金额 -> 估算输出 -> 授权 -> 交换。
- 做基础异常处理：余额不足、授权失败、滑点过大。

### 必读资料

- Uniswap Docs（Contracts）: <https://docs.uniswap.org/contracts/v2/overview>
- v2-periphery: <https://github.com/Uniswap/v2-periphery>

### 视频资料

- Bilibili - Uniswap V2 前端代码解析 Part 1: <https://www.bilibili.com/video/BV1Uv411N7Ry>

### 当日产出

- 可演示页面录屏 1 段。

***

## Day 9：测试与安全边界

### 学习任务

- 为关键逻辑补测试：报价、滑点、deadline、revert 分支。
- 理解常见攻击面：抢跑、MEV、授权风险。

### 必读资料

- v2-core 测试目录: <https://github.com/Uniswap/v2-core/tree/master/test>
- v2-periphery 测试目录: <https://github.com/Uniswap/v2-periphery/tree/master/test>

### 视频资料

- YouTube - Finematics 频道: <https://www.youtube.com/c/Finematics/videos>

### 当日产出

- 至少 3 个测试用例说明文档。

***

## Day 10：进入 Uniswap V3 心智模型

### 学习任务

- 理解集中流动性、价格区间、Tick 概念。
- 对比 V2 与 V3 的核心差异。

### 必读资料

- Uniswap V3 Core: <https://github.com/Uniswap/v3-core>
- Uniswap V3 白皮书: <https://app.uniswap.org/whitepaper-v3.pdf>
- Uniswap V3 Book: <https://uniswapv3book.com/>

### 视频资料

- Bilibili - Uniswap V3 白皮书解读（Rebase相关合集可查）: <https://space.bilibili.com/32808851>

### 当日产出

- 一页对比表：V2 vs V3（流动性、费率、资产效率）。

***

## Day 11：V3 合约与仓库结构

### 学习任务

- 阅读 v3-core 与 v3-periphery 目录结构。
- 确认核心交互入口与 Position 管理角色。

### 必读资料

- v3-core: <https://github.com/Uniswap/v3-core>
- v3-periphery: <https://github.com/Uniswap/v3-periphery>
- Dapp-Learning: <https://github.com/Dapp-Learning-DAO/Dapp-Learning>

### 视频资料

- Bilibili - Rebase 频道: <https://space.bilibili.com/32808851>

### 当日产出

- 一张图：V3 中 Pool 与 Position 的关系。

***

## Day 12：工程脚手架实战

### 学习任务

- 跑通 Scaffold-ETH 2，创建本地链并部署示例合约。
- 在前端页面完成一次完整交互。

### 必读资料

- Scaffold-ETH 2: <https://github.com/scaffold-eth/scaffold-eth-2>

### 视频资料

- YouTube - Scaffold-ETH 相关教程检索入口: <https://www.youtube.com/results?search_query=scaffold-eth+2+tutorial>

### 当日产出

- 一份启动与部署步骤记录。

***

## Day 13：最小 DEX 学习项目收敛

### 学习任务

- 整理一个最小 Demo：报价、授权、交换、交易回执展示。
- 补足错误提示与边界处理。

### 必读资料

- v2-periphery: <https://github.com/Uniswap/v2-periphery>
- viem: <https://github.com/wevm/viem>
- wagmi: <https://github.com/wevm/wagmi>

### 视频资料

- Bilibili - Uniswap 前端解析视频: <https://www.bilibili.com/video/BV1Uv411N7Ry>

### 当日产出

- Demo 仓库 README 初版。

***

## Day 14：复盘与下一阶段规划

### 学习任务

- 复盘 14 天中所有关键概念与坑点。
- 输出下一阶段主题：聚合器、跨链、永续合约、MEV 防护。

### 必读资料

- Uniswap 文档主页: <https://docs.uniswap.org/>
- Uniswap GitHub 组织: <https://github.com/Uniswap>

### 视频资料

- YouTube - Uniswap 官方频道: <https://www.youtube.com/@Uniswap>
- Bilibili - Rebase 频道: <https://space.bilibili.com/32808851>

### 当日产出

- 一份《下一阶段 30 天学习计划》草稿。

***

## 每周验收标准

- 第 1 周：能清晰解释 V2 的 swap/mint/burn 逻辑。
- 第 2 周：能独立实现最小前端交互并完成一次真实流程演示。
- 进阶：能说明 V3 相比 V2 的核心价值与代价。

## 补充建议

- 优先“少而深”：每次只跟 1 条调用链，不要同时开多个协议。
- 每天记录“一个业务问题 + 一个代码证据 + 一个结论”。
- 只要遇到不确定就回到源码和测试，不靠二手总结。

