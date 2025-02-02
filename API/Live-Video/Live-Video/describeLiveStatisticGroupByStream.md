# describeLiveStatisticGroupByStream


## 描述
查询流分组统计数据

## 请求方式
GET

## 请求地址
https://live.jdcloud-api.com/v1/describeLiveStatisticGroupByStream


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**domainName**|String|True| |播放域名|
|**appName**|String|True| |应用名称|
|**streamName**|String|True| |流名称|
|**ispName**|String|False| |[运营商](../Reference/Operator.md)|
|**locationName**|String|False| |[地域](../Reference/Region.md) ，如beijing,shanghai。多个用逗号分隔<br>|
|**period**|String|False| |查询周期，当前取值范围：“oneMin,fiveMin,halfHour,hour,twoHour,sixHour,day,followTime”，分别表示1min，5min，半小时，1小时，2小时，6小时，1天，跟随时间。默认为空，表示fiveMin。当传入followTime时，表示按Endtime-StartTime的周期，只返回一个点<br>|
|**startTime**|String|True| |起始时间<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>|
|**endTime**|String|False| |结束时间:<br>- UTC时间<br>  格式:yyyy-MM-dd'T'HH:mm:ss'Z'<br>  示例:2018-10-21T10:00:00Z<br>- 为空,默认为当前时间，查询时间跨度不超过1天<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**result**|Result| |
|**requestId**|String|requestId|

### Result
|名称|类型|描述|
|---|---|---|
|**dataList**|LiveStatisticGroupByStreamResult[]| |
### LiveStatisticGroupByStreamResult
|名称|类型|描述|
|---|---|---|
|**startTime**|String|起始时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**endTime**|String|结束时间点，UTC时间，格式：yyyy-MM-dd'T'HH:mm:ss'Z'<br>|
|**data**|LiveStatisticGroupByStreamResultData[]| |
### LiveStatisticGroupByStreamResultData
|名称|类型|描述|
|---|---|---|
|**streamName**|String|流名称<br>|
|**playerCount**|Long|在线人数<br>|
|**bandwidth**|Long|带宽，单位：bps<br>|
|**maxBandwidthtime**|Long|带宽峰值时间点，单位：秒<br>|
|**flow**|Long|流量，单位:Byte<br>|

## 返回码
|返回码|描述|
|---|---|
|**200**|OK|
|**400**|Invalid parameter|
|**401**|Authentication failed|
|**404**|Not found|
|**500**|Internal server error|
|**503**|Service unavailable|

## 请求示例
GET
```
https://live.jdcloud-api.com/v1/describeLiveStatisticGroupByStream?domainName=yourdomain&appName=yourapp&streamName=yourstream&startTime=2018-10-21T10:00:00Z&&endTime=2018-10-22T10:00:00Z

```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41", 
    "result": {
        "dataList": [
            {
                "data": [], 
                "endTime": "2019-06-14T08:50:00Z", 
                "startTime": "2019-06-14T08:45:00Z"
            }, 
            {
                "data": [
                    {
                        "bandwidth": 808894, 
                        "flow": 30333530, 
                        "maxBandwidthtime": 1560502500, 
                        "playerCount": 1, 
                        "streamName": "test105"
                    }, 
                    {
                        "bandwidth": 635065, 
                        "flow": 23814941, 
                        "maxBandwidthtime": 1560502500, 
                        "playerCount": 1, 
                        "streamName": "test106"
                    }
                ], 
                "endTime": "2019-06-14T08:55:00Z", 
                "startTime": "2019-06-14T08:50:00Z"
            }, 
            {
                "data": [
                    {
                        "bandwidth": 1224631, 
                        "flow": 45923689, 
                        "maxBandwidthtime": 1560502800, 
                        "playerCount": 1, 
                        "streamName": "test105"
                    }, 
                    {
                        "bandwidth": 1326398, 
                        "flow": 49739930, 
                        "maxBandwidthtime": 1560502800, 
                        "playerCount": 1, 
                        "streamName": "test106"
                    }
                ], 
                "endTime": "2019-06-14T09:00:00Z", 
                "startTime": "2019-06-14T08:55:00Z"
            }
        ]
    }
}
```
