---
sidebar_position: 6
---

# signTypedData(EIP-712) 与验签

## signTypedData([EIP-712](https://eips.ethereum.org/EIPS/eip-712))

```tsx
const typedData; // The Typed Data to Sign
// Sign V4 Typed Data
const signature = await smartAccount.signTypedData(
  typedData.domain,
  typedData.types,
  typedData.message
); // Sign message
// Verify V4 Typed Data
```

## 验签

```tsx
import { verifyTypedData } from "@unipasswallet/smart-account-validator";

const isValid = await verifyTypedData({
  // Verify Message
  typedData,
  signature,
  provider,
  address: await smartAccount.getAddress(),
});
```