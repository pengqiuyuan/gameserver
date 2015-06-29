礼品卡API
===================



生成礼品卡
-------------

```
post /api/gameserver/v1/gift/add
请求体
{
	"userId":"1",                //礼品卡生成人
	"serverZoneId":"1",         //大区Id
	"gameId":"1",             //项目Id
	"server":["1","2",...],
	"playerId":["1","2",...],       //限制玩家Id GUID
	"category":"1",            //礼品码类型
	"number":"1000",          //礼品码生成数量  
	"giftItems":[{              //道具 
		"id":"1",	             //金币Id
		"number":"9999"      //金币数量
	},{
		"id":"2",	  //钻石Id
		"number":"9999"      //钻石数量
	},...],
	"begindate":1423524111000,     //礼品卡生效时间 Long 毫秒
	"enddate":1423787228000，     //礼品卡结束时间  Long  毫秒
	"status":"0"                      //礼品卡状态 0审核中 1已同意 2被拒绝
}
响应
{
	"status":"success"
}

```

礼品卡列表
-------------

```
GET /api/gameserver/v1/gift/index
参数 
     category: 1 (超级管理员) 0(普通GM) （0、普通用户此项目下当前gm的礼品卡列表    1、超级管理员此项目下下所有gm的礼品卡列表）
     gameId: 项目Id 
     userId: GMId 
响应
[{
	"giftId":"1",               //礼品卡id
	"userId":"1",              //礼品卡生成人
	"gameId":"1",            //项目Id
	"number":"1000",         //礼品码生成数量  
	"giftItems":[{             //道具 
		"id":"1",	            //金币Id
		"number":"9999"     //金币数量

	},{
		"id":"2",	                    //钻石Id
		"number":"9999"             //钻石数量
	},...],                		
	"begindate":1423524111000,     //礼品卡生效时间 Long 毫秒
	"enddate":1423787228000，     //礼品卡结束时间  Long  毫秒
	"status":"0"                      //礼品卡状态 0审核中 1已同意 2被拒绝
},...]

```

删除礼品卡
-------------

```
GET /api/gameserver/v1/gift/delete
请求体
{
    "giftIds": [
        "1",	                       //礼品卡Id
        "2",
        ...
    ]
}
响应 ：
成功
{
	"status":"success"
}
失败
{
	"status":"false"
}

```

导出礼品码
-------------

```
GET /api/gameserver/v1/gift/export 
参数 giftId 礼品卡Id
响应
[
    {
        "id": "FB1234567890"
    },
    {
        "id": "FB1234567891"
    },
    ...
]

```

审核礼品卡
-------------

```
GET GET /api/gameserver/v1/gift/review
参数 giftId 礼品卡Id
     status 0     礼品卡状态 0审核中 1已同意 2被拒绝
响应
成功
{
	"status":"success"
}
失败
{
	"status":"false"
}

```

查询礼品卡
-------------

```
GET GET GET /api/gameserver/v1/gift/search
参数 status 查询方式 0为GUID 
                    1为礼品码Id 
		            2为礼品卡Id
     query  1  FB1234567890 1
     gameId: 项目Id

status 为 0
响应
[{
	"giftcode":"FB1234567890" //礼品码
	"giftId":"1",             //礼品卡id
	"userId":"1",             //礼品卡生成人
	"guid":"1",               //GUID
	"platformId":"1",             //平台Id
	"begindate":1423524111000,    //使用时间 
	"channelId":"123"               //渠道Id
},...]

status 为 1
响应
礼品码已存在已使用
[{
	"giftcode":"FB1234567890" //礼品码
	"giftId":"1",             //礼品卡id
	"userId":"1",             //礼品卡生成人
	"guid":"1",               //GUID
	"platformId":"1",             //平台Id
	"begindate":1423524111000,    //使用时间 
	"channelId":"123"               //渠道Id
	"status":"2"
}]

礼品码已存在未使用
[{"status":"1"}]

礼品码不存在
[]

status 为 2
响应
{
	"number":"3"          //此礼品卡已使用礼品码数量，number 为 -1 是表示此礼品卡不存在
}

```

根据礼品卡Id，查询礼品卡
-------------

```
GET /api/gameserver/v1/gift/searchgift
参数 giftId 礼品卡Id
响应
存在
{
	"giftId":"1",                       //礼品卡id
	"userId":"1",                      //礼品卡生成人
	"gameId":"1",                    //项目Id
	"number":"1000",                 //礼品码生成数量  
	"giftItems":[{                     //道具 
		"id":"1",	                     //金币Id
		"number":"9999"              //金币数量
	},{
		"id":"2",	                     //钻石Id
		"number":"9999"              //钻石数量
	},...],                		
	"begindate":1423524111000,      //礼品卡生效时间 Long 毫秒
	"enddate":1423787228000，      //礼品卡结束时间  Long  毫秒
	"status":"0"                       //礼品卡状态 0审核中 1已同意 2被拒绝
}

不存在
{}

```

