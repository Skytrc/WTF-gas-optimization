# WTF Gas Optimization

Solidity gas optimization techniques, using Foundry. 总结写 Solidity 智能合约更省 gas 的技巧。

## 大纲

[1. use constant and immutable](#1-use-constant-and-immutable)

[2. use calldata over memory](#2-use-calldata-over-memory)

[3. use Bitmap](#3-use-bitmap)

[4. use unchecked](#4-use-unchecked)

[5. use uint256 over uint8](#5-use-uint256-over-uint8)

[6. use revert over require and assert](#5-use-uint256-over-uint8)

## 1. use constant and immutable

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/01_Constant/Constant.sol) |[文章](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/01_Constant/readme.md)

**Testing**

```
forge test --contracts 01_Constant/Constant.t.sol --gas-report
```

**Gas report**

| Function Name    | Gas Cost |
| ---------------- | -------- |
| varConstant      | 183      |
| **varImmutable** | 161 ✅   |
| variable         | 2305     |

## 2. use calldata over memory

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/02_CalldataAndMemory/CalldataAndMemory.sol) | [文章](https://github.com/WTFAcademy/WTF-gas-optimization/tree/main/02_CalldataAndMemory/readme.md)

**Testing**

```
forge test --contracts 02_CalldataAndMemory/CalldataAndMemory.T.sol --gas-report
```

**Gas report**

| Function Name       | Gas Cost |
| ------------------- | -------- |
| **writeByCalldata** | 67905 ✅ |
| writeByMemory       | 68456    |

## 3. use Bitmap

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/03_Bitmap/Bitmap.sol) | [文章](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/03_Bitmap/readme.md)

**Testing**

```
forge test --contracts 03_Bitmap/Bitmap.T.sol --gas-report
```

**Gas report**

| Function Name         | Gas Cost |
| --------------------- | -------- |
| **setDataWithBitmap** | 22366 ✅ |
| setDataWithBoolArray  | 35729    |

## 4. use unchecked

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/04_Unchecked/Unchecked.sol) | [文章](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/04_Unchecked/readme.md)

**Testing**

```
forge test --contracts 04_unchecked/Unchecked.T.sol --gas-report
```

**Gas report**

| Function Name    | Gas Cost  |
| ---------------- | --------- |
| forNormal        | 1910309   |
| **forUnckecked** | 570287 ✅ |

## 5. use uint256 over uint8

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/05_Uint/Uint.sol) | [文章](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/05_Uint/readme.md)

**Testing**

```
forge test --contracts 05_uint/Uint.T.sol --gas-report
```

**Gas report**

| Function Name    | Gas Cost |
| ---------------- | -------- |
| read Uint8       | 2379     |
| read Uint128     | 2465     |
| **read Uint256** | 2317 ✅  |
| set Uint8        | 5355     |
| set Uint128      | 5358     |
| **set Uint256**  | 5322 ✅  |

## 6. use revert over require and assert

[代码](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/06_Error/Error.sol) | [文章](https://github.com/WTFAcademy/WTF-gas-optimization/blob/main/06_Error/readme.md)

**Testing**

```
forge test --contracts 06_Error/Error.T.sol --gas-report
```

**Gas report**

| Error Name | Gas Cost |
| ---------- | -------- |
| Assert     | 180      |
| Require    | 268      |
| Revert     | 164 ✅   |



## WTF Gas Optimization 贡献者

<div align="center">
  <h4 align="center">
    贡献者是WTF学院的基石
  </h4>
<a href="https://github.com/WTFAcademy/WTF-gas-optimization/graphs/contributors">
  <img src="https://contrib.rocks/image?repo=WTFAcademy/WTF-gas-optimization" />
</a>
</div>
