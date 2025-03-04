---
sidebar_position: 3
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# 使用 RainbowKit

## Demo

A demo app for RainbowKit is available [here](https://up-rainbowkit-demo.vercel.app/), and source code is available too: [Demo Code](https://github.com/UniPassID/rainbowkit-demo).

## 安装


<Tabs>
<TabItem value="npm">

```shell
npm install @unipasswallet/rainbowkit-plugin wagmi
```

</TabItem>
<TabItem value="yarn">

```shell
yarn add @unipasswallet/rainbowkit-plugin wagmi
```

</TabItem>
</Tabs>

## 参数

* `chains` -- Chains supported by app. This is the same parameter as would be passed to other RainbowKit wallets..

* `options.connect` -- Connection options for the default networkId, name of the app.

* `options.connect.chainId` -- Default chainId.

* `options.connect.returnEmail` -- If true, email will return when connect function been called.

* `options.connect.appSettings` -- Config appName, appIcon and theme.

* `options.connect.rpcUrls` -- Config mainnet and testnet rpc URLs. In the local development environment, you don't need to fill in, this will use our default test URLs, but in the production environment, you need to fill in with your own rpc node url.

## 用例

```ts
    import { configureChains, createClient, WagmiConfig } from "wagmi";
    import {
    optimismGoerli,
    arbitrumGoerli,
    goerli,
    polygonMumbai,
    } from "wagmi/chains";
    import { publicProvider } from "wagmi/providers/public";
    import { unipassWallet } from "@unipasswallet/rainbowkit-plugin";

    const connectors = connectorsForWallets([
        {
        groupName: "Recommended",
        wallets: [
            injectedWallet({ chains, shimDisconnect: true }),
            metaMaskWallet({ chains, shimDisconnect: true }),
            rainbowWallet({ chains }),
            unipassWallet({
            chains,
            connect: {
                chainId: polygonMumbai.id,
                returnEmail: false,
                appSettings: {
                    appName: "wagmi demo",
                    appIcon: "your icon url",
                },
                rpcUrls: {
                    mainnet: "your eth mainnet rpc url",
                    polygon: "your polygon mainnet rpc url",
                    bscMainnet: "your bsc mainnet rpc url",
                    rangersMainnet: "your rangers mainnet rpc url",
                    arbitrumMainnet: "your arbitrum mainnet rpc url",

                    polygonMumbai: "your polygon testnet rpc url",
                    goerli: "your goerli testnet rpc url",
                    bscTestnet: "your bsc testnet rpc url",
                    rangersRobin: "your rangers testnet rpc url",
                    arbitrumTestnet: "your arbitrum testnet rpc url",
                },
            },
            }),
        ],
        },
    ]);

    const wagmiClient = createClient({
        autoConnect: true,
        connectors,
        provider,
    });
```

## 验签

服务器端验签可参考：[**UniPass Verifying Messages**](../verifying-messages/01-unipass-verifying-messages.mdx)。