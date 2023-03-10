
# 代付

当前通道：**gk**

| 区域 | 通道（可点击切换）|
| --- |-----------------------------------------------------|
| 墨西哥 | [sp](代付(sp).html)|
| 菲律宾 | [601](代付(601).html)|
| 肯尼亚 | [gk](代付(gk).html)|
| 坦桑尼亚 | [gt](代付(gt).html)

## 请求地址
https://[[域名]](../help/区域域名.html)/i/transfer/create

## 请求方式
POST

## 请求头
Content-Type:application/json

## 请求参数

| 字段名 | 参数名 | 类型 | 必填 | 示例 | 描述 |
|-----|-----|-----|-----|-----|-----|
|商户号 | merchant_code | String | 是 | 100012 | 商户后台分配的商户号(商户系统->账户信息获取) |
|商户订单号 | merchant_order_no | String | 是 | 456545645487 | 商户系统商户订单号，要求32个字符内 |
|支付通道编码|pay_type|String|是|gk|示例中的固定值|
|币种|currency|String|是|KES|肯尼亚先令|
|金额|amount|String|是|100.00|单位(元)，保留两位小数|
|电话号码 | mobile | String | 是 | 254743123003 |必须保证手机号真实性，代付会根据手机号入账。 |
|邮箱|email|String|是|xxx@gmail.com|收款人邮箱|
|姓名|name|String|是|jack|收款人姓名|
|回调地址|notify_url|String|是|https://www.xxx.com/notify | 付款成功后支付系统通过该地址通知支付结果 |
|签名|sign|String|是|9a55c3868b414cdc740068420a2d3q00 |[签名算法](../rule/签名算法.html)|

## 请求示例

```json
{
    "merchant_code": "100012",
    "merchant_order_no": "20230223111540234080",
    "pay_type": "gk",
    "currency": "KES",
    "amount": "100.00",
    "notify_url": "https:\/\/www.uwinpay.com\/api\/notify",
    "name": "test",
    "mobile": "645631281",
    "email": "admin@qq.com",
    "sign": "0b136b72c88f495400caf72d864b90f4"
}
```

## 返回结果

|字段名|参数名|类型|必填|示例|描述|
|-----|-------------------------|-----|-----|-----|-----|
|响应状态|code|String|是|success|success/fail/error|
|请求信息|msg|String|是|ok|返回的请求信息|
|数据体|data|Object|是|-|以下为数据体属性|
|平台订单号|data>>order_no|String|是|20210226165044236|系统生成的平台订单号|
|商户订单号|data>>merchant_order_no|String|是|10226165044236|商户系统商户订单号，要求32个字符内|
|商户号|data>>merchant_code|String|是|GKggRpDN6|商户后台分配的商户号(商户系统->账户信息获取)|
|金额|data>>amount|String|是|100.00|单位(元)，保留两位小数|
|实际金额|data>>reality_amount|String|是|100.00|单位(元)，保留两位小数|
|订单状态|data>>order_status|Number|是|2|[参数说明](../help/参数说明.html#订单状态)|
|下单时间戳|data>>order_time|Number|是|1663402686|精确到秒|
|签名|data>>sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 响应示例

```json
{
  "code": "success",
  "data": {
    "merchant_code": "100012",
    "merchant_order_no": "20221202071204771165",
    "amount": "199.10",
    "reality_amount": "199.10",
    "order_status": 0,
    "order_no": "20221202071232169671",
    "order_time": 1669983152,
    "sign": "73e849d7d5c8d38c4410f3bd66487813"
  },
  "msg": "ok"
}
```
