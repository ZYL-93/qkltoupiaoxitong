# 区块链投票系统 (Blockchain Voting System)

这是一个基于以太坊区块链的去中心化投票应用（DApp）。

## 项目简介

本项目包含两个主要部分：

1. **Blockchain (`/blockchain`)**: 使用 Hardhat 框架开发的智能合约后端，负责投票逻辑的链上实现。
2. **Frontend (`/frontend`)**: 使用 Vue 3 + Vite + Ethers.js 开发的前端界面，用户可以通过 MetaMask 钱包与合约交互进行投票。

## 快速开始 (从零运行指南)

按照以下步骤，你可以从零开始在本地运行整个项目。

### 1. 环境准备

确保你的电脑已安装：

- [Node.js](https://nodejs.org/) (建议 v16 或更高版本)
- [MetaMask](https://metamask.io/) 浏览器插件

### 2. 启动区块链网络

1. 打开终端（Terminal 1）。
2. 进入 blockchain 目录：
   ```bash
   cd blockchain
   ```
3. 安装依赖：
   ```bash
   npm install
   ```
4. 启动本地区块链节点：
   ```bash
   npx hardhat node
   ```
   > **注意**：保持此终端一直运行，不要关闭！它会模拟一个本地的以太坊网络，并列出 20 个测试账户及其私钥。

### 3. 部署智能合约

1. 打开一个新的终端（Terminal 2）。
2. 进入 blockchain 目录：
   ```bash
   cd blockchain
   ```
3. 部署合约到本地网络：
   ```bash
   npx hardhat run scripts/deploy.js --network localhost
   ```
4. **关键步骤**：部署完成后，终端会显示类似 `Voting contract deployed to: 0x...` 的信息。**复制这个合约地址**。

### 4. 配置前端

1. 使用编辑器打开文件 `frontend/src/contracts/VotingABI.js`。
2. 找到 `export const CONTRACT_ADDRESS = "..."` 这一行。
3. 将刚才复制的合约地址粘贴进去，替换原有的地址，然后保存文件。
   - 示例：`export const CONTRACT_ADDRESS = "0x5FbDB2315678afecb367f032d93F642f64180aa3";`

### 5. 启动前端应用

1. 在 Terminal 2 中（或新开终端），进入 frontend 目录：
   ```bash
   cd ../frontend
   ```
   _(如果你当前在 blockchain 目录，使用 `cd ../frontend`；如果在根目录，使用 `cd frontend`)_
2. 安装依赖：
   ```bash
   npm install
   ```
3. 启动开发服务器：
   ```bash
   npm run dev
   ```
4. 终端会显示一个访问链接（通常是 `http://localhost:5173`），在浏览器中打开它。

### 6. MetaMask 设置与使用

为了能进行投票，你需要配置 MetaMask 连接到你的本地区块链。

1. 打开浏览器中的 MetaMask 插件。
2. **添加本地网络**（如果尚未添加）：
   - 点击左上角网络选择下拉框 -> "添加网络" -> "手动添加网络"。
   - **网络名称**：Localhost 8545
   - **RPC URL**：`http://127.0.0.1:8545`
   - **链 ID**：`31337`
   - **货币符号**：ETH
   - 点击保存并切换到该网络。
3. **导入测试账户**：
   - 回到 Terminal 1（运行 `npx hardhat node` 的那个终端）。
   - 复制其中任意一个账户的 **Private Key**（私钥 string，不要复制 Account 地址）。
   - 在 MetaMask 中点击顶部账户名 -> "添加账户或硬件钱包" -> "导入账户"。
   - 粘贴私钥并导入。
4. 现在你应该能看到账户里有 10000 ETH（测试币）。连接账户到网站，即可开始投票！
