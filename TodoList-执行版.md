# DEX 学习 TodoList（执行版）

## 使用说明

- 每天学习后，只做两件事：勾选已完成项 + 写 3 行复盘。
- 每个任务都要有可验证产出（笔记、流程图、脚本、录屏、测试其一）。
- 每周至少安排 1 次回顾，把“看懂但不会用”的点转成下一周待办。

---

## 第一阶段：Web3 基础概念（扫盲）

### 1) 钱包与地址

- [ ] 说清楚私钥、公钥、地址三者关系（100 字以内）。
- [ ] 完成一次钱包创建与备份演练（测试钱包）。
- [ ] 能解释“谁拥有资产控制权”以及助记词风险。
- [ ] 画出“签名 -> 广播 -> 上链确认”最小流程图。

资料：
- Ethereum 账户文档：https://ethereum.org/zh/developers/docs/accounts/
- MetaMask 学习中心：https://learn.metamask.io/
- ECDSA 基础（可选进阶）：https://cryptobook.nakov.com/digital-signatures/ecdsa-sign-verify-messages

### 2) 代币标准（重点 ERC-20）

- [ ] 阅读 ERC-20 标准并列出 6 个核心方法/事件。
- [ ] 区分 `transfer`、`approve`、`transferFrom` 的调用场景。
- [ ] 能解释 allowance 的作用和常见风险。
- [ ] 在区块浏览器中查看一个真实代币的合约与事件日志。

资料：
- ERC-20 标准：https://eips.ethereum.org/EIPS/eip-20
- OpenZeppelin ERC20 文档：https://docs.openzeppelin.com/contracts/5.x/erc20
- 区块浏览器（以太坊）：https://etherscan.io/

### 3) 交互逻辑（Gas / Approve / Swap）

- [ ] 解释 Gas Fee、Gas Limit、Gas Price、Base Fee 的区别。
- [ ] 能说明为什么 DEX 里常见“先 Approve 再 Swap”。
- [ ] 理解 `amountOutMin` 与 `deadline` 的保护意义。
- [ ] 复盘 1 笔真实交易（看懂 input data、状态、手续费）。

资料：
- Gas 机制（EIP-1559）：https://ethereum.org/zh/developers/docs/gas/
- Uniswap V2 合约总览：https://docs.uniswap.org/contracts/v2/overview
- Uniswap 路由参考：https://docs.uniswap.org/contracts/v2/reference/smart-contracts/router-02

阶段完成标准：
- [ ] 可以完整口述一次“钱包签名 + 授权 + 兑换”的链上流程。
- [ ] 输出《Web3 基础扫盲笔记》1 份。

---

## 第二阶段：DEX 核心机制（Uniswap V2）

- [ ] 理解 AMM 与 x*y=k，不看资料能举例解释滑点。
- [ ] 阅读 Factory/Pair/Router 的职责边界。
- [ ] 精读 `swap`、`mint`、`burn` 三个核心路径。
- [ ] 写出一版 `swap` 伪代码并标注关键校验点。
- [ ] 完成 1 张 V2 调用链路图（前端到链上）。

资料：
- V2 Core：https://github.com/Uniswap/v2-core
- V2 Periphery：https://github.com/Uniswap/v2-periphery
- V2 白皮书：https://uniswap.org/whitepaper.pdf

阶段完成标准：
- [ ] 能独立解释“报价、成交价、滑点、手续费”关系。

---

## 第三阶段：前端与链上交互闭环

- [ ] 搭一个最小页面：连接钱包 + 读取报价。
- [ ] 串起输入金额 -> 授权 -> 兑换流程。
- [ ] 补充失败场景处理：余额不足、授权失败、滑点过大。
- [ ] 增加交易状态展示：pending / success / revert。
- [ ] 录制 1 段可演示视频（30-90 秒）。

资料：
- viem：https://github.com/wevm/viem
- wagmi：https://github.com/wevm/wagmi
- Uniswap 文档入口：https://docs.uniswap.org/

阶段完成标准：
- [ ] 页面可跑通 1 次完整兑换（测试网或本地环境）。

---

## 第四阶段：进阶与工程化

- [ ] 建立至少 3 个关键测试用例（报价/滑点/deadline）。
- [ ] 了解常见风险：MEV、抢跑、授权管理。
- [ ] 初步理解 Uniswap V3（集中流动性、Tick、区间仓位）。
- [ ] 输出一页 V2 vs V3 对比表。

资料：
- Uniswap V3 Core：https://github.com/Uniswap/v3-core
- Uniswap V3 Book：https://uniswapv3book.com/
- V3 白皮书：https://app.uniswap.org/whitepaper-v3.pdf

阶段完成标准：
- [ ] 完成个人《DEX 学习复盘》1 份（问题、方法、下一步）。

---

## 每日执行模板（复制使用）

- 日期：
- 今日目标（不超过 3 条）：
  - [ ]
  - [ ]
  - [ ]
- 今日产出（链接/文件名）：
- 阻塞点：
- 明日第一件事：
