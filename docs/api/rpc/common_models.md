# CommonModels

:::tip Maintainer
[TiantaoZhu](https://github.com/TiantaoZhu) && [lyd00](https://github.com/lyd00)
:::

## RpcAccountInfo
```json ::Demo
{
    "accountAddress": "vite_f84b6eede43969a938dfd1c381e197ed47dd06f329b7c92328",
    "totalNumber": "433",
    "tokenBalanceInfoMap": {
        "tti_8816f463487a9cc3c3886b8c": {
            "tokenInfo": {
                "tokenName": "as",
                "tokenSymbol": "aa",
                "totalSupply": "10000",
                "decimals": 19,
                "owner": "vite_f84b6eede43969a938dfd1c381e197ed47dd06f329b7c92328",
                "pledgeAmount": "10000",
                "withdrawHeight": "12"
            },
            "totalAmount": "132",
            "number": "10000"
        }
    }
}
```
`tokenBalanceInfoMap: [tokentypeid]TokenBalanceInfo`

|  Name  | JSON type | Actual type |Description |
|:------------:|:-----------:|:-----:|:-----:|
| accountAddress |  string | Address| Account address|
| totalNumber | string | uint64| The total transaction number of the account|
| tokenBalanceInfoMap | map | map| Token balance map|

`TokenBalanceInfo`
|  Name  | JSON type | Actual type |Description |
|:------------:|:-----------:|:-----:|:-----:|
| tokenInfo |  tokenInfo | tokenInfo| Token information|
| totalAmount | string | bigint| Token balance|
| number | string | uint64| The total transaction number for the specific token and account|

`tokenInfo`
|  Name  | JSON type | Actual type |Description |
|:------------:|:-----------:|:-----:|:-----:|
| tokenName |  string | string| Token name|
| tokenSymbol | string | string| Token symbol|
| totalSupply | string | bigint| Total supply|
| decimals | string | uint8| The smallest separable token unit|
| owner | string | address| Token issuer|
| tokenId | string | TokenTypeId| Token ID|




## AccountBlock
|  Name  | JSON type | Actual type |Description |
|:------------:|:-----------:|:-----------:|:-----:|
| blockType | Byte | Byte | Block type (1->request(create contract). 2->request(transfer). 3->request(claim SBP rewards). 4->response. 5->response(failed). 6->request(refund by contract). 7->response(genesis). 1, 2, 3 and 6 are request. 4, 5 and 7 are response. Specifically, common transfer has request block type 2 and response block type 4)|
| hash | hex string | Hash | The hash of transaction|
| prevHash |hex string| Hash | The hash of previous transaction in the account chain. `0000000000000000000000000000000000000000000000000000000000000000` if no previous transaction in the account|
| accountAddress| string | Address | Account address|
| publicKey|base64 string | []byte | The public key of whom the block was produced|
| fromAddress |string| Address | The address of whom the transaction was sent from. For response only|
| toAddress|string | Address | The address of whom the transaction is sent to. For request only|
| fromBlockHash |hex string |  Hash | The hash of request transaction. For response only, otherwise `0000000000000000000000000000000000000000000000000000000000000000` is filled|
| tokenId |string |TokenTypeId | The token ID in which the transaction is settled|
| snapshotHash | hex string | Hash | The hash of snapshot block which the transaction refers to |
| data | string| []byte | Additional data which the transaction may carry |
| timestamp | int64 | int64 | Transaction time(in seconds)|
| logHash | hex string | Hash  | The hash of smart contract LogList |
| nonce | base64 string |[]byte] | PoW nonce |
| signature | base64 string| []byte] | Transaction signature |
| height | string | uint64 | Transaction height |
| quota | string | uint64 | The quota consumed by the transaction |
| amount |string|  big.Int | Transaction amount |
| fee | string | big.Int | Transaction fee |
| confirmedTimes |string| uint64 | The confirmation number of the transaction |
| tokenInfo | tokenInfo | tokenInfo | The token information in which the transaction is settled|
