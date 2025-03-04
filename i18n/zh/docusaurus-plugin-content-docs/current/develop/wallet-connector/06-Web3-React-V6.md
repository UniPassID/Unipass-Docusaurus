---
sidebar_position: 6
---

import Tabs from '@theme/Tabs';
import TabItem from '@theme/TabItem';

# 使用 Web3-React V6

## Demo

A demo app for web3-react V6 is available [here](https://up-web3-react-v6-demo.vercel.app/), and source code is available too: [Demo Code](https://github.com/UniPassID/we3-react-v6-demo).

## 安装

<Tabs>
<TabItem value="npm">

```shell
npm install @unipasswallet/web3-react-v6-connector
```

</TabItem>
<TabItem value="yarn">

```shell
yarn add @unipasswallet/web3-react-v6-connector
```

</TabItem>
</Tabs>

## 参数

* `options.connect.chainId` -- Default chainId.

* `options.connect.returnEmail` -- If true, email will return when connect function been called.

* `options.connect.appSettings` -- Config appName, appIcon and theme.

* `options.connect.rpcUrls` -- Config mainnet and testnet rpc URLs. In the local development environment, you don't need to fill in, this will use our default test URLs, but in the production environment, you need to fill in with your own rpc node url.

## 用例

```ts
import { providers } from "ethers";
import { Web3ReactProvider } from "@web3-react/core";

function getLibrary(provider: any): providers.Web3Provider {
  return new providers.Web3Provider(provider);
}

export default function Layout() {
  return (
    <Web3ReactProvider getLibrary={getLibrary}>
      <App />
    </Web3ReactProvider>
  );
}

```
```ts
import { useWeb3React } from "@web3-react/core";
import { UniPassConnector } from "@unipasswallet/web3-react-v6-connector";

export const unipassConnector = new UniPassConnector({
  chainId: 80001,
  returnEmail: false,
  appSettings: {
    appName: "Web3 React Demo app",
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
});

const { active, library, activate, account, chainId, deactivate } = useWeb3React();

const connect = async () => {
  try {
    await activate(unipassConnector, () => {}, true);
  } catch (e) {
    console.error(e);
  }
};
```

## 验签

服务器端验签可参考：[**UniPass Verifying Messages**](../verifying-messages/01-unipass-verifying-messages.mdx)。