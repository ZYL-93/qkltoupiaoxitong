步骤 1: 完全停止所有服务
bash

# 停止所有运行中的终端

# Ctrl+C 停止所有 npm/hardhat 进程

步骤 2: 彻底清除 MetaMask 缓存
在 MetaMask 中：

打开 MetaMask
设置 → 高级 → 重置账户 (Reset Account)
确认重置
关闭 MetaMask 窗口
步骤 3: 清除浏览器缓存
在浏览器中：

按 Ctrl + Shift + Delete
选择"缓存的图片和文件"
时间范围选择"全部时间"
点击"清除数据"
或者使用硬刷新：

按 Ctrl + Shift + R 或 Ctrl + F5
步骤 4: 重新启动完整流程
终端 1：启动 Hardhat Node

bash
cd d:\benkeshengxm\qkltoupiaoxitong\blockchain
npx hardhat node
终端 2：部署合约

bash
cd d:\benkeshengxm\qkltoupiaoxitong\blockchain
npx hardhat run scripts/deploy.js --network localhost
终端 3：启动前端

bash
cd d:\benkeshengxm\qkltoupiaoxitong\frontend
npm run dev
步骤 5: 重新连接
打开浏览器（新标签页）
访问前端地址
连接 MetaMask
尝试投票
