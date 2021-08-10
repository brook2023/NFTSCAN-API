# NFTSCAN对外开发API
## API_HEADER

http://eth.ditanbao.cc:18760

## NEST最新报价信息查询

请求链接

http://eth.ditanbao.cc:18760/block/0xc83E009c7794e8f6d1954dc13c23A35Fc4D039F6/

返回参数


| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| new_block_height | long | 最新区块高度 |
| server_time | String | 服务器当前时间 |
| token_block | long | 上一笔报价所在区块 |
| token_contract | String | 合约地址 |
| token_gasPrice | long | 上一笔报价的gas |
| token_symbol | String | Symbol |

{
    "new_block_height":11254725,
    "server_time":"2020-11-14 16:25:22",
    "token_block":11254724,
    "token_contract":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
    "token_gasPrice":23100000000,
    "token_symbol":"NEST"
}


## NEST Pending数据查询

请求链接

http://eth.ditanbao.cc:18760/pending/0xc83E009c7794e8f6d1954dc13c23A35Fc4D039F6/

返回参数


| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| best_gas_price | long | 当前最佳GAS |
| mempool_count | int | pengding未确认报价交易数量 |
| token_contract | String | 报价合约地址 |
| token_symbol | String | Symbol |
| tx_gas_price | long | Pending未确认报价交易的GAS，多笔取最高 |


{
    "best_gas_price":15000000000,
    "mempool_count":1,
    "token_contract":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
    "token_symbol":"NEST",
    "tx_gas_price":18585001529
}

## NEST报价历史记录查询（返回最近50条）

请求链接

http://eth.ditanbao.cc:18760/history/0xc83E009c7794e8f6d1954dc13c23A35Fc4D039F6/

返回参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| contract| string | 报价合约地址 |
| mempool_count | ArrayList | 最近50条报价记录 |


data数据

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| block_number | String | 交易所在区块 |
| contract | String | 合约地址 |
| from | String | 报价地址 |
| gas | String |  |
| gas_price | String |  |
| nonce | String |  |
| symbol | String |  |
| to | String | 报价合约地址 |
| txid | String | 交易ID |
| value | String | 金额 |


{
    "contract":"0xc83E009c7794e8f6d1954dc13c23A35Fc4D039F6",
    "data":[
        {
            "block_number":"11254604",
            "contract":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
            "from":"0xa2bd7c849247a6f5ae590180ed45e46795a07b09",
            "gas":"600000",
            "gas_price":"14700000000",
            "is_error":"0",
            "nonce":"19380",
            "symbol":"NEST",
            "to":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
            "txid":"0x732128e424c9ff67f439c6f4b97272b954fd10e1930f6d7e4c7be94bf96a37e3",
            "value":"0x1a19527938b810000"
        }
    ]
}


## nToken最新报价信息查询

### 请求链接和NEST一致，替换合约地址就行，返回数据一致
目前支持的nToken（HBTC HT WBTC DAI HUSD YFI YFIII UNI）

##### 查询最新报价信息
http://eth.ditanbao.cc:18760/block/token合约地址/
##### 查询pending
http://eth.ditanbao.cc:18760/pending/token合约地址/
##### 查询历史记录
http://eth.ditanbao.cc:18760/history/token合约地址/

#### HBTC为例
##### 查询最新报价信息
http://eth.ditanbao.cc:18760/block/0x0316eb71485b0ab14103307bf65a021042c6d380/
##### 查询pending
http://eth.ditanbao.cc:18760/pending/0x0316eb71485b0ab14103307bf65a021042c6d380/
##### 查询历史记录
http://eth.ditanbao.cc:18760/history/0x0316eb71485b0ab14103307bf65a021042c6d380/


错误信息

{"contract":"0xc83E009c7794e8f6d1954dc13c23A35Fc4","message":"invalid contract address"}
