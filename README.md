# NFTSCAN对外开发API
##接口描述 

NFTSCAN对外开发接口分为免费版和付费版。
免费版本在官网注册账户后可获得一个API链接，请求上限为1000次/天。
付费版可根据需求选择不同上限请求套餐。
定制版请联系NFTSCAN官方团队，提供websocket方式,pending数据等服务。eeee


| 请求次数/天 | 费用(USDC) | 等级 |
| :-----:| :----: | :----: |
| 1000 | 免费 | V0 |
| 2000 | XXXX | V1 |
| 10000 | XXXX | V2 |
| 30000 | XXXX | V3 |
| 60000 | XXXX | V4 |
| 定制 | 定制 | V5 |

API链接示例

http://api.nftscan.com/nft/8f6d1954dc13c23A35F


## 查询地址持有NFT资产

请求链接

nft/address/message/0xc83E009c7794e8f6d1954dc13c23A35Fc4D039F6

返回参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| status | int | 返回状态 |
| code | int | 状态码 |
| time | String | 时间 |
| message | String | 消息 |
| nft_platform_num | int | NFT项目数量 |
| nft_platform_list | List | NFT项目列表 |


### nft_platform_list
| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_platform_name | String | NFT项目名称 |
| nft_platform_type | String | NFT项目类型 |
| nft_platform_contract | String | NFT项目合约地址 |
| nft_platform_describe | String | NFT项目简介 |
| nft_list | List | NFT资产列表 |

### nft_list

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_asset_id | String | NFT资产ID |
| nft_creator | String | NFT铸造发起地址 |
| nft_holder | String | NFT资产当前持有者 |
| nft_create_time | String | NFT铸造时间 |
| nft_creat_hash | String | NFT铸造hash |
| nft_content_uri | String | NFT元数据链接 |
| nft_detail | String | NFT详情 |


数据示例



```json
{
    "status":0,
    "code":2001,
    "time":"2020-11-14 16:25:22",
    "message":"请求次数超过限制",
    "nft_platform_num":2,
    "nft_platform_list":[
        {
            "nft_platform_name":"UNI",
            "nft_platform_type":"1155/721",
            "nft_platform_contract":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
            "nft_platform_describe":"UNI is .....",
            "nft_list":[
                {
                    "nft_asset_id":11254725,
                    "nft_creator":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
                    "nft_holder":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
                    "nft_create_time":1628601074,
                    "nft_creat_hash":"0xcd6025bdedd26b8cae645348389158b805ee4341369e0c3c84d129ccbe529eac",
                    "nft_content_uri":"https://lh3.googleusercontent.com/ECp1wSceVbzN9XBhO4wkse7AwccKoN6ecXVuWwsM4t3m8kNxeYDGLPzIKq3LHxTFxazJYnBGJxhY5vc3_s4ss3Eupg9RPTiGFf93-A",
                    "nft_detail":"{\"image\":\"ipfs://QmNQdLr39xXRpr6XghhAD1fd1dntJouugvFhYqQVebMUku\"}"
                }
            ]
        }
    ]
}
```


## 查询交易记录

请求链接

根据地址和NFT项目合约查询地址在项目上交易记录

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| user_address | String | 用户地址 |
| nft_address | String | NFT合约地址 |

nft/record/user_address/nft_address

根据地址、NFT项目合约、NFT tokenid,查询地址在项目上具体某个NFT交易记录

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| user_address | String | 用户地址 |
| nft_address | String | NFT合约地址 |
| token_id | String | NFT资产ID |

nft/record/user_address/nft_address/token_id


根据NFT项目合约查询该平台下所有交易记录

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_address | String | NFT合约地址 |

nft/record/nft_address

多条需要分页（单页条数是否固定？数据实时更新问题）



返回参数


| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| status | int | 返回状态 |
| code | int | 状态码 |
| time | String | 时间 |
| message | String | 消息 |
| nft_total_num | String | 记录总量 |
| nft_page_size | int | 当前页码 |
| nft_record_list | List | 记录列表 |


### nft_record_list

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| tx_from_address | String | 发起地址 |
| tx_to_address | String | 执行地址 |
| tx_send_address | String | 发送地址 |
| tx_recive_address | String | 接收地址 |
| tx_token_id | String | NFT资产ID |
| tx_time | String | 交易时间 |
| block_number | String | 所在区块高度 |
| block_hash | String | 所在区块hash |
| nonce | String | nonce |
| gas_limit | String | Gas Limit |
| gas_price | String | Gas |
| gas_used | String | Gas Used |
| status | String | 状态 |
| logs | String | 交易完整日志（查询平台记录） |



数据示例
```json
{
    "status":0,
    "code":2001,
    "time":"2020-11-14 16:25:22",
    "message":"成功",
    "nft_contract_address":"0x04f23ffaddddd335d3df6172d876e192fddd0eae",
    "nft_total_num":10,
    "nft_page_size":10,
    "nft_record_list":[
        {
            "tx_from_address":"0x3df364ed7e8a887f7f9c240f7e281a4ea05ce03f",
            "tx_to_address":"0x04f23ffaddddd335d3df6172d876e192fddd0eae",
            "tx_send_address":"0x04f23ffaddddd335d3df6172d876e192fddd0eae",
            "tx_recive_address":"0x3df364ed7e8a887f7f9c240f7e281a4ea05ce03f",
            "tx_token_id":"172",
            "tx_time":"0x60fe4952",
            "block_number":"0x60fe4952",
            "block_hash":"0xd90c8b6d1867009370f9bea85d1b589a7e8582cf1cdfee927ee738e4e20420c2",
            "tx_hash":"0x72458bcaa8e9cb94509737b42f118e169a5b63713c800c6205319912a2950b10",
            "nonce":"0x6c088e200",
            "gas_limit":"0x6c088e200",
            "gas_price":"0x37d49",
            "gas_used":"0x9b577",
            "status":"0x1",
            "logs":"待定"
        }
    ]
}
```




## 查询单个NFT资产信息

请求参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_address | String | NFT合约地址 |
| token_id | String | NFT资产ID |

nft/message/nft_address

返回参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| status | int | 返回状态 |
| code | int | 状态码 |
| time | String | 时间 |
| message | String | 消息 |
| nft_message | Object | NFT详细信息 |

nft_message

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_asset_id | String | NFT资产ID |
| nft_creator | String | NFT铸造发起地址 |
| nft_holder | String | NFT资产当前持有者 |
| nft_create_time | String | NFT铸造时间 |
| nft_creat_hash | String | NFT铸造hash |
| nft_content_uri | String | NFT元数据链接 |
| nft_detail | String | NFT详情 |


数据示例

```json
{
    "status":0,
    "code":2001,
    "time":"2020-11-14 16:25:22",
    "message":"请求次数超过限制",
    "nft_message":{
        "nft_asset_id":11254725,
        "nft_creator":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
        "nft_holder":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
        "nft_create_time":1628601074,
        "nft_creat_hash":"0xcd6025bdedd26b8cae645348389158b805ee4341369e0c3c84d129ccbe529eac",
        "nft_content_uri":"https://lh3.googleusercontent.com/ECp1wSceVbzN9XBhO4wkse7AwccKoN6ecXVuWwsM4t3m8kNxeYDGLPzIKq3LHxTFxazJYnBGJxhY5vc3_s4ss3Eupg9RPTiGFf93-A",
        "nft_detail":"{\"image\":\"ipfs://QmNQdLr39xXRpr6XghhAD1fd1dntJouugvFhYqQVebMUku\"}"
    }
}
```


## 查询NFT平台下所有资产信息

请求参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_address | String | NFT合约地址 |


nft/total_message/nft_address

返回参数

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| status | int | 返回状态 |
| code | int | 状态码 |
| time | String | 时间 |
| message | String | 消息 |
| nft_message_List | Object | NFT详细信息列表，时间近到远 |

nft_message_List

| 参数名称 | 类型 | 描述 |
| :-----:| :----: | :----: |
| nft_asset_id | String | NFT资产ID |
| nft_creator | String | NFT铸造发起地址 |
| nft_holder | String | NFT资产当前持有者 |
| nft_create_time | String | NFT铸造时间 |
| nft_creat_hash | String | NFT铸造hash |
| nft_content_uri | String | NFT元数据链接 |
| nft_detail | String | NFT详情 |


数据示例

```json
{
    "status":0,
    "code":2001,
    "time":"2020-11-14 16:25:22",
    "message":"请求次数超过限制",
    "nft_message_List":[
        {
            "nft_asset_id":11254725,
            "nft_creator":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
            "nft_holder":"0xc83e009c7794e8f6d1954dc13c23a35fc4d039f6",
            "nft_create_time":1628601074,
            "nft_creat_hash":"0xcd6025bdedd26b8cae645348389158b805ee4341369e0c3c84d129ccbe529eac",
            "nft_content_uri":"https://lh3.googleusercontent.com/ECp1wSceVbzN9XBhO4wkse7AwccKoN6ecXVuWwsM4t3m8kNxeYDGLPzIKq3LHxTFxazJYnBGJxhY5vc3_s4ss3Eupg9RPTiGFf93-A",
            "nft_detail":"{\"image\":\"ipfs://QmNQdLr39xXRpr6XghhAD1fd1dntJouugvFhYqQVebMUku\"}"
        }
    ]
}
```

