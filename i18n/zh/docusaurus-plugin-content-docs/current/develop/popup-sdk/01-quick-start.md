---
sidebar_position: 1
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# 快速开始

Popup SDK 是连接 UniPass Wallet 页面的 javascript SDK 工具包，提供了一系列的方法供第三方应用与 UniPass Wallet 进行交互。

<Tabs>
<TabItem value="npm">

```bash
npm install --save @unipasswallet/popup-sdk
```

</TabItem>
<TabItem value="yarn">

```bash
yarn add @unipasswallet/popup-sdk
```

</TabItem>
</Tabs>

## 相关资料

- [Popup SDK GitHub](https://github.com/UniPassID/unipass-popup-sdk)
- [Online Demo](https://popup-demo.wallet.unipass.id/)
- [Demo 源码](https://github.com/UniPassID/unipass-popup-sdk/tree/main/examples/demo)

:::tip
当前 Demo 调用的 UniPass Wallet 网址：[https://testnet.wallet.unipass.id/](https://testnet.wallet.unipass.id/login)
:::

## 历史版本

| 更新版本 | 重大变更        | 更新日期   | 更新说明                                                                               |
| -------- | --------------- | ---------- | -------------------------------------------------------------------------------------- |
| v1.1.8 | --               | 2023.04.13 | 为登录方法添加 forceLogin 参数，默认为 false，若 forceLogin 为 true，连接时将强制用户进行登录流程 |
| v1.1.7 |                      | 2023.04.04    | Ethereum Provider 新增对kcc 及 avax 的支持 |
| v1.1.6 |                      | 2023.03.30    | 新增对 kcc 及 avax 的支持 |
| v1.1.5 |                      | 2023.03.28    | 清除无用的控制台日志 |
| v1.1.4 |                      | 2023.03.03    | 新特性：弹窗被阻止时添加 tips 浮窗，可用于点击打开弹窗 |
| v1.1.3 |                      | 2023.03.01    | 移除对 buffer^6.0.3 的依赖 |
| v1.1.2 |                      | 2023.02.24    | 为登出方法添加deep参数，若deep为true，将会打开UniPass钱包登出 |
| v1.1.1 |                      | 2023.02.14    | 支持 arbitrum network |
| v1.1.0 |                      | 2023.02.13    | 为ethereum-provider包新增rpcUrls参数，用户可传入自定义rpc节点url |
| v1.0.2 |                      | 2023.02.06    | login方法新增authorize参数，用于 sign with ethereum |
| v1.0.1 |                      | 2023.02.01    | 新增对标准SDK支持 |
| v0.0.11 |                     | 2022.12.16   | 新增 storageType 参数 |
| v0.0.10 |                     | 2022.12.14   | 新增 signTypedData(EIP712) 和 isValidTypedSignature 方法|
| v0.0.9   | --              | 2022.11.25 | 优化 SDK 初始化传参数, 减少非必要参数                           |
| v0.0.8   | --              | 2022.11.18 | 修复登录后，无法发送交易 (报错: can not authorize without login) 的问题                |
| v0.0.7   | **Breaking change** | 2022.11.15 | 支持 Google 第三方登录，增加连接钱包返回 Email 的可选功；signMessage 增加 unipass 前缀 |
| v0.0.4   | --              | 2022.10.14 | isValidSignature 增加 account 可选参数                                                 |
| v0.0.1   | --              | 2022.10.09 | 支持连接钱包获取地址，转账原生代币和 ERC20 代币，签名/验签等功能。                     |