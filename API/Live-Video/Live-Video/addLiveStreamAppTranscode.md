# addLiveStreamAppTranscode


## 描述
添加应用转码配置
- 添加应用级别的转码模板配置


## 请求方式
POST

## 请求地址
https://live.jdcloud-api.com/v1/transcodeApps:config


## 请求参数
|名称|类型|是否必需|默认值|描述|
|---|---|---|---|---|
|**publishDomain**|String|True| |推流域名|
|**appName**|String|True| |应用名称|
|**template**|String|True| |转码模版<br>- 取值范围: 系统标准转码模板, 用户自定义转码模板<br>- 系统标准转码模板<br>  ld (h.264/640 * 360/15f)<br>  sd (h.264/960 * 540/25f)<br>  hd (h.264/1280 * 720/25f)<br>  shd (h.264/1920 * 1080/30f)<br>  ld-265 (h.265/640 * 360/15f)<br>  sd-265 (h.265/960 * 540/25f)<br>  hd-265 (h.265/1280 * 720/25f)<br>  shd-265 (h.265/1920 * 1080/30f)<br>|


## 返回参数
|名称|类型|描述|
|---|---|---|
|**requestId**|String|requestId|


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
POST
```
https://live.jdcloud-api.com/v1/transcodeApps:config

```
```
{
    "appName": "yourapp", 
    "publishDomain": "push.yourdomain.com", 
    "template": "shd"
}
```

## 返回示例
```
{
    "requestId": "bgvmivir54gddpgi764se9f4kfr7ge41"
}
```
