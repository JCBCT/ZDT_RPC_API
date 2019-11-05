## 1. 调用返回区块链总体信息
### chain/get_info
```
调用参数：
    无

返回值：
get_info调用的返回结果是一个JSON对象，包含当前所连接ZDT链的总体信息，成员如下：
    server_version：节点版本
    head_block_num：链头区块序号
    lase_irreversible_block_num：最后不可逆区块号
    head_block_id：链头区块ID
    head_block_time：链头区块生成时间
```
### 示例代码
```
调用请求：
    ~$ curl -X POST --url http://rpc.zdtchain.com:8888/v1/chain/get_info
返回结果：
    {
      "server_version":"01341592",
      "chain_id":"0ee3efef949cbe8f00c36eba9ec591dc1b9d256fb01dc64a29b1ab36c7c37b9c",
      "head_block_num":23990253,
      "last_irreversible_block_num":23990184,
      "last_irreversible_block_id":"016e0fa87dd05ba6186bd5b02b6b8d379b69b168bb6b4d5bb29da2aceaf9d61b",
      "head_block_id":"016e0feda49db6502034aaf1243e7f829b0dee575c729d5bbf39b8e0144a9532",
      "head_block_time":"2019-11-01T06:36:52.000","head_block_producer":"optovxdsfkvg",
      "virtual_block_cpu_limit":200000000,
      "virtual_block_net_limit":1048576000,
      "block_cpu_limit":199900,
      "block_net_limit":1048576,
      "server_version_string":"v1.0.0"
    }
```

## 2. 调用返回指定账户的代币余额信息
### chain/get_currency_balance 
```
调用参数：
JSON对象，用来声明查询参数，其成员如下：
    code：代币合约托管账户名称，字符串
    account：要查询账户的名称，字符串
    symbol：要查询的代码符号，字符串
    
返回值：
    get_currency_balance调用返回指定账号所持有的代币余额。
```
### 示例代码
```
调用请求：
~$ curl -X POST --url http://rpc.zdtchain.com:8888/v1/chain/get_currency_balance -d '{
  "code":"tonydchan123",
  "symbol":"ZING",
  "account":"dvy1opao3uoh"
}'

返回结果：
["24351.70660000 ZING"]
```

## 3. 调用返回指定的交易数据
### transaction
```
调用参数：
JSON对象，声明要查询的交易，其成员如下：
    id：交易ID，字符串
    
返回值：
    transaction调用的返回值为查询到的交易描述JSON对象。
```
### 示例代码
```
调用请求：
~$ curl -X GET --url：http://api.zdtchain.com/transaction?trx_id=b4a0634ffbc459563010f4bba5e9ab74cb12897f2b0b719147836cba1be55291

返回结果：
[{
    "trx_id":"b4a0634ffbc459563010f4bba5e9ab74cb12897f2b0b719147836cba1be55291",
    "actions":[{
        "data":{
            "from":"3fo4rl15bxw5",
	    "to":"wwagwz2l1hxr",
	    "quantity":"0.17000000 ZING",
	    "memo":"share_12"
	}
    }],
    "irreversible":true,
    "block_id":"016db15332e10493595048f5ad78bd05f378418632bfefdc5588344ddc530a16",
    "block_num":23966035
}]
```


## 4. 调用返回指定地址的交易记录
### action
```
调用参数：
JSON对象，声明要查询的交易地址，其成员如下：
    address：交易地址，字符串
    
返回值：
    transaction调用的返回值为查询到的交易记录描述JSON对象。
```
### 示例代码
```
调用请求：
~$ curl -X GET --url：http://api.zdtchain.com/action?name=c1jpp2fwf3v4&size=20&page=1&token=zom.token

返回结果：
{
	"size": 20,
	"page": 1,
	"total": 12,
	"items": [{
		"act": {
			"data": {
				"from": "c1jpp2fwf3v4",
				"to": "evxbfghgxxzd",
				"quantity": "1990.00000000 ZOM",
				"memo": "u4ebf"
			}
		},
		"trx_id": "7cf52d85570ff32989be1f1d97aeb9c67e33930d3f2c2bbe28b777263abe1a63",
		"block_num": 24678137,
		"block_time": "2019-11-05T06:09:14.000"
	}, {
		"act": {
			"data": {
				"from": "c1jpp2fwf3v4",
				"to": "2lgcmpz2rztk",
				"quantity": "10.00000000 ZOM",
				"memo": "destroy"
			}
		},
		"trx_id": "7cf52d85570ff32989be1f1d97aeb9c67e33930d3f2c2bbe28b777263abe1a63",
		"block_num": 24678137,
		"block_time": "2019-11-05T06:09:14.000"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "859.96000000 ZOM",
				"memo": "share_15"
			}
		},
		"trx_id": "4fccd26f2250e42cd3974aa58c6474fae76f0aed12adb2acd777ceba4eec3802",
		"block_num": 24535926,
		"block_time": "2019-11-04T10:24:08.500"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "263.16000000 ZOM",
				"memo": "share_14"
			}
		},
		"trx_id": "3b3ec07977b8e86d876c5c179d70981824e6a0bf076336c503ca6793cc0165fa",
		"block_num": 24535915,
		"block_time": "2019-11-04T10:24:03.000"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "867.52000000 ZOM",
				"memo": "share_8"
			}
		},
		"trx_id": "63b78a1137cac16533395b4b066604770293e5aff2d91369d81e21c934566ed1",
		"block_num": 24337926,
		"block_time": "2019-11-03T06:54:08.500"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "88.50000000 ZOM",
				"memo": "share_6"
			}
		},
		"trx_id": "562d92ceec74f0ed7209dcef51e3dd3b557c1eeabdd6f24469a05f0b7a3d52ed",
		"block_num": 24337915,
		"block_time": "2019-11-03T06:54:03.000"
	}, {
		"act": {
			"data": {
				"from": "c1jpp2fwf3v4",
				"to": "evxbfghgxxzd",
				"quantity": "174.12500000 ZOM",
				"memo": "u4ebf"
			}
		},
		"trx_id": "966a24ab092b1ba2da16fa8cb5af53ed4f99bb84b3e73f58219cba91a3eaaec1",
		"block_num": 24301825,
		"block_time": "2019-11-03T01:53:18.000"
	}, {
		"act": {
			"data": {
				"from": "c1jpp2fwf3v4",
				"to": "2lgcmpz2rztk",
				"quantity": "0.87500000 ZOM",
				"memo": "destroy"
			}
		},
		"trx_id": "966a24ab092b1ba2da16fa8cb5af53ed4f99bb84b3e73f58219cba91a3eaaec1",
		"block_num": 24301825,
		"block_time": "2019-11-03T01:53:18.000"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "15.36280000 ZOM",
				"memo": "cost"
			}
		},
		"trx_id": "c7a0e802b73694e197ff1e7c28a9c3d482d8571d99e29a038cfeb3aefdda36a6",
		"block_num": 24240834,
		"block_time": "2019-11-02T17:25:02.500"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "0.68000000 ZOM",
				"memo": "share_3"
			}
		},
		"trx_id": "253e97052df23d6e52d76a1faaed3bda22cf8392cef7720687429fa86429f77a",
		"block_num": 23971435,
		"block_time": "2019-11-01T04:00:03.000"
	}, {
		"act": {
			"data": {
				"from": "2lgcmpz2rztk",
				"to": "c1jpp2fwf3v4",
				"quantity": "75.47830000 ZOM",
				"memo": "cost"
			}
		},
		"trx_id": "a85bb393a58fc961dd593f663d45821b3e76b60bfe065fbec6072b4d20e00fe6",
		"block_num": 22685633,
		"block_time": "2019-10-24T17:25:02.000"
	}, {
		"act": {
			"data": {
				"from": "upojfuze4arb",
				"to": "c1jpp2fwf3v4",
				"quantity": "85.20000000 ZOM",
				"memo": "cost"
			}
		},
		"trx_id": "5e0abd82f35f3d5d70ef0ce53bba84140cf7ddb6ba367a8a1f6e80ad42f9970e",
		"block_num": 20043949,
		"block_time": "2019-10-09T10:31:00.000"
	}]
}

```

## 5. 调用返回指定区块的数据
### chain/get_block
```
调用参数：
一个JSON对象，用来指定要提取数据的区块，其成员如下：
    block_num_or_id：字符串，要提取数据的区块序号或ID
    
返回值：
get_block调用返回描述指定区块数据的JSON对象，其成员如下：
    previous：前一个区块的ID，字符串
    timestamp：区块时间戳，时间字符串
    producer：出块账号，字符串
    schedule_version：调度器版本，数值
    new_producers：新出现的出块账号集合，空或数组
    producer_signature：出块账号的签名，字符串
    regions：分区集合，数组
    input_transactions：区块中包含的交易集合，数组
    id：区块ID，字符串
    block_num：区块序号，整数
    ref_block_prefix：参考块前缀，整数
```
### 示例代码
```
调用请求：
~$ curl -X POST --url http://rpc.zdtchain.com:8888/v1/chain/get_block -d '{
  "block_num_or_id": "016e34a103fad1e20b2de4bc415b29606aac75e5a02fa773d3171991fc3576e6"
}'

返回结果：

{
    "timestamp":"2019-11-01T07:55:10.000",
    "producer":"fnscxfgszvpk",
    "confirmed":0,
    "previous":"016e34a001f489021cbf44e2aabc2a5316ec7bf4ace3c7b94e83d75bf09043ab",
    "transaction_mroot":"0000000000000000000000000000000000000000000000000000000000000000",
    "action_mroot":"cb246523ab6a1bf059a02ed74980cad7984c326d0e54f89b7085c2c194088eae",
    "schedule_version":1,
    "new_producers":null,
    "header_extensions":[],
    "producer_signature":"SIG_K1_KZAKpgBFsq8XkovPw1up6oRqjzxxMBhNpJdLgf9NktCT4St7QhUooevCr1Wv4nFzVWcSpzU5dyH8AJXyqCG9qbJeHbgwX3",
    "transactions":[],
    "block_extensions":[],
    "id":"016e34a103fad1e20b2de4bc415b29606aac75e5a02fa773d3171991fc3576e6",
    "block_num":23999649,
    "ref_block_prefix":3169070347
}
```

## 6. 调用返回指定账号的描述信息
### chain/get_account
```
调用参数：JSON对象，用来指定要读取信息的账号，其成员如下：
    account_name：账号名称，字符串
    
返回值：et_account调用的返回值是描述账号信息的JSON对象，其成员如下：
	account_name：账号名称
	permissions: 账号权限集合，权限对象数组，每个权限对象的成员如下：
	perm_name：权限名称
	parent：父权限名称
	required_auth：授权条件，JSON对象，成员如下：
	threshold：阈值，整数
	keys：公钥信息集合，数组，每个公钥信息对象成员如下：
	key：公钥，字符串
	weight：权重
	accounts：账号数组
```
### 示例代码
```
调用请求：
~$ curl -X POST --url http://rpc.zdtchain.com:8888/v1/chain/get_account -d '{
  "account_name": "wwagwz2l1hxr"
}'

返回结果：
{
    "account_name":"wwagwz2l1hxr",
    "head_block_num":24008717,
    "head_block_time":"2019-11-01T09:10:44.000",
    "privileged":false,
    "last_code_update":"1970-01-01T00:00:00.000",
    "created":"2019-08-12T11:02:15.000",
    "ram_quota":41192,"net_weight":1000,
    "cpu_weight":1000,
    "net_limit":{
        "used":129,
	"available":446751401,
	"max":446751530
     },
    "cpu_limit":{
        "used":458,
	"available":85210634,
	"max":85211092
    },
    "ram_usage":4580,
    "permissions":[{
	"perm_name":"active",
	"parent":"owner",
	"required_auth":{
            "threshold":1,
	    "keys":[{
	        "key":"ZDT7LcP7kKYG77jzydXDyCQpstSxbhQaYa9N25xfFUqSqG9oC4FyW",
		"weight":1
	    }],
	    "accounts":[],
	    "waits":[]
       }},
       {
	    "perm_name":"owner",
	    "parent":"",
            "required_auth":{"threshold":1,
            "keys":[{
	        "key":"ZDT7m6GVAxXjx9VV8EBEHTBeqfRhJTobiuKXk4e62xZAgFsv1EYQM",
	        "weight":1
	    }],
	    "accounts":[],
	    "waits":[]}
    }],
    "total_resources":{
        "owner":"wwagwz2l1hxr",
	"net_weight":"0.1000 ZDT",
	"cpu_weight":"0.1000 ZDT",
	"ram_bytes":39792
    },
    "self_delegated_bandwidth":null,
    "refund_request":null,
    "voter_info":null
}
```

## 7. 调用将指定的交易提交到链上
**备注：将指定的交易提交到链上，请参考EOS参数标准。**
### chain/push_transaction 
```
调用参数：
JSON对象，声明交易、签名等信息，成员如下：
    signatures：array of strings，签名数组
    compression：boolean，是否压缩格式，布尔类型，默认值：false
    packed_context_free_data：string，上下文无关的数据
    packed_tx：string，序列化的交易数据
    
返回值：
    push_transaction调用的返回结果包含交易ID。
```
### 示例代码
```
调用请求：
~$ curl -X POST --url http://rpc.zdtchain.com:8888/v1/chain/push_transaction -d '{
  ...
}'

返回结果：
{
    'transaction_id' = "1..."
}
``` 

