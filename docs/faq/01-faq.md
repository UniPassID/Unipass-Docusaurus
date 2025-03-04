---
sidebar_position: 1
---

import Image from '@theme/IdealImage';
import thumbnail_1 from './img/meta-transaction.png';

# FAQ

## Advantages & Differences

### Benefits of UniPass Wallet over EOA Wallet

UniPass Wallet offers `improved user conversion rates` and `asset security` with the following benefits:

- **Easy generation**: UniPass Wallet can be generated without the need for mnemonics, simplifying the process for Web2 users and lowering the awareness threshold.
- **Social recovery**: Unlike the EOA wallet, UniPass Wallet supports social recovery, allowing users to regain control of their accounts with the aid of guardians even if they lose control of their wallet due to a major breach.
- **Gasless experience**: Users can enjoy a gasless experience in UniPass Wallet, which reduces the burden of early game participation and prevents user attrition.
- **Versatile features**: UniPass Wallet can incorporate versatile and potent features like off-chain authorization and on-chain transactions, without requiring users to modify their addresses.

### Verifying a Signature with UniPass Wallet and EOA Wallet Differences

To verify the UniPass Wallet signature on the chain, the application contract can call the UniPass Wallet contract to verify it according to the **[EIP-1271](https://eips.ethereum.org/EIPS/eip-1271)** protocol, which must be supported in application contracts.

On-chain signature verification differences:
- Contract Wallet: The contract needs to support the EIP-1271 protocol and then directly call the contract wallet's signature verification interface through the EIP-1271 protocol.
- EOA Wallet: Verify the Secp256k1 signature directly in the contract.

---

## About Master key

### How is the master key generated?

The master key is generated through MPC-TSS calculation by client and server slices. It only contains a public key, not a private key.

### Where is the master key stored?

`client slice` creates a keystore file, which is encrypted with the user's password using `scrypt` on the client side. This keystore file is stored in UniPass cloud storage and can be saved to third-party cloud drives or locally.

`Server slices` are encrypted with AWS's HSM (Hardware Security Module) and produced independently for each account. UniPass can only access them with the user's 2FA.

In summary, the master key's lack of a corresponding private key eliminates the risk of private key leaks. Additionally, the client and server slices use separate security schemes, making it highly unlikely for both to be cracked and matched at the same time.

---

## About Relayer

### What is the role and authority of Relayer?

Relayers submit transactions and pay for gas on behalf of the user. They can't modify the operation in the user's signature.

### What is the principle and implementation of gasless?

The [**Meta Transaction**](https://medium.com/coinmonks/ethereum-meta-transactions-101-de7f91884a06) method allows for a gasless experience.

<p align="center">
    <Image img={thumbnail_1} width="80%"/>
</p>

In the smart contract wallet solution, the user's account is a contract on-chain. It has an in-built authentication method to verify the user's signature. The user signs an account operation and signature, which is not a Layer 1 transaction but a basic operation. This is wrapped by anyone into a full Layer 1 transaction, submitted to the chain, and paid for gas. This signed operation is called a meta-transaction.

The contract wallet aims to change the smart contract's state via a Layer 1 transaction on the chain. The transaction must include two signature parts. The user's signature in the data field for their desired operation is verified by the contract and can only be signed by the user. The other part is the relayer's signature, who submits the Layer 1 transaction to the chain and pays the gas. The relayer can be anyone and is a required part of a standard transaction.

---

## What can I do if UniPass closed

### Can UniPass Wallet be exported to traditional wallets?

UniPass Wallet is a smart contract wallet, which means it cannot directly export traditional private keys or seed phrases. However, users can transfer control of the contract to a MetaMask address.

### How to migrate to MetaMask when UniPass stop working?

UniPass has an email-based social recovery mechanism, which can be performed without any help from UniPass or third parties. If the UniPass bot fails, users can download an open-source front-end or use a web form with IPFS hosting to recover their account. The steps are:

1. Input your email address/UniPass account address.
2. Input the destination address (e.g. a MetaMask address) that you want to use to control your UniPass account in the future.
3. Click the ‘Generate’ button to get an email template (subject & body) and send it to your guardians’ email addresses.
4. Ask your guardians to forward the email they received back to your email address. If you are also using your own email as a guardian, you can send the email template to any email address that you can receive.
5. Download the email files (.eml) from your inbox and upload them with this front-end and also the help with your MetaMask to the blockchain. Done.