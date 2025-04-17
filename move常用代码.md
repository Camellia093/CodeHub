

# sui _move

## 区块链浏览器

- https://suivision.xyz/

## 将Windows文件上传 与 解压

```
cp /mnt/d/Yao05/Downloads/sui-testnet-v1.47.0-ubuntu-aarch64.tgz /usr/lib/sui-testnet
```

```
tar -zxvf sui-testnet-v1.47.0-ubuntu-aarch64.tgz
```

输入 `cd /mnt/d` 然后按回车键。这就像是你走进了 Windows 这个房间的大门（D 盘）

## 绑定钱包

```
sui keytool import <私钥> <签名方案>
```

签名方案——ed25519, secp256k1, secp256r1
用这个命令导入你的钱包地址
私钥在钱包里面导出

## 查看管理钱包地址

```
sui client addresses 
```

切换当前活跃钱包地址

```
sui client switch --address <要切换到的地址>
```

查看当前钱包余额

```
sui client gas
```

发布项目

```
sui client publish [--gas-budget 10000000]  # []内为可选项
```

