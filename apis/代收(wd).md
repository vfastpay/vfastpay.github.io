# 代收

当前通道：**wd**

| 区域 | 通道（可点击切换）                                     |
| --- |-----------------------------------------------|
| 巴西 | [iugu](代收.html)                           |
| 印度 | [dd](代收(dd).html)&nbsp;&nbsp; [wd](代收(wd).html)|
| 菲律宾 | [cs](代收(cs).html)&nbsp;&nbsp; [lf](代收(lf).html) |
| 墨西哥 | [sp](代收(sp).html)|
| 越南 | [ly](代收(ly).html)|
| 印度尼西亚 | [wa](代收(wa).html)

## 请求地址
https://[[域名]](../help/区域域名.html)/i/pay/create

## 请求方式
POST

## 请求头
Content-Type:application/json

## 请求参数

| 字段名 | 参数名 | 类型  | 必填  | 示例值 | 描述  |
|--|-----|-----|-----|-----|-----|
|商户号|merchant_code|String|是|100012|商户后台分配的商户号(商户系统->账户信息获取)|
|商户订单号|merchant_order_no|String|是|221201bx01010|商户系统商户订单号，要求32个字符内|
|支付通道编码|pay_type|String|是|wd|示例中的固定值|
|币种|currency|String|是|INR|示例中的固定值|
|姓名|name|String|是|Jack|付款人姓名|
|电话号码|mobile|String|是|5213562778893|付款人联系方式|
|邮箱|email|String|是|xxxxx@google.com|付款人邮箱|
|金额|amount|String|是|200|单位(元)，保留两位小数|
|回调地址|notify_url|String|是|https://www.xxx.com/notify|付款成功后支付系统通过该地址通知支付结果|
|成功转向地址|page_url|String|是|https://www.xxxxx.com/paysuccess|支付成功的返回页面|
|下单时间戳|order_time|Number|是|1663402686|精确到秒|
|签名|sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 请求示例

```json
{
    "merchant_code": "100012",
    "merchant_order_no": "20230103093027907097",
    "pay_type": "wd",
    "currency": "INR",
    "name": "test",
    "mobile": "09456312891",
    "email": "gmail@gmail.com",
    "amount": "100.00",
    "notify_url": "https:\/\/www.uwinpay.com\/api\/public\/index.php\/wepay\/pay_notify",
    "page_url": "test",
    "order_time": 1672709427,
    "sign": "6b431411983e4840845555a009c54665"
}
```

## 返回结果

|字段名|参数名|类型|必填|示例| 描述                             |
|-----|-------------------------|-----|-----|-----|--------------------------------|
|响应状态|code|String|是|success| success/fail/error|
|请求信息|msg|String|是|ok| 返回的请求信息|
|数据体|data|Object|是|-| 以下为数据体属性|
|商户号|data>>merchant_code|String|是|GKggRpDN6|商户后台分配的商户号(商户系统->账户信息获取)|
|平台订单号|data>>order_no|String|是|20221201133641400317|系统生成的平台订单号|
|商户订单号|data>>merchant_order_no|String|是|20221201133714239179|商户系统商户订单号，要求32个字符内|
|金额|data>>amount|String|是|100.00|单位(元)，保留两位小数|
|实际金额|data>>reality_amount|String|是|100.00|单位(元)，保留两位小数|
|订单状态|data>>order_status|Number|是|2| [参数说明](../help/参数说明.html#订单状态) |
|支付链接|data>>pay_data|String|是|https://xxx.xxx.com/pay|返回给C端用户打开的支付链接|
|下单时间戳|data>>order_time|Number|是|1663402686| 精确到秒                           |
|签名|data>>sign|String|是|9a55c3868b414cdc740068420a2d3q00| [签名算法](../rule/签名算法.html)      |

## 响应示例

```json
{
  "code": "success",
  "data": {
      "merchant_code": "100012",
      "merchant_order_no": "20230103093027907097",
      "amount": "100.00",
      "reality_amount": "100.00",
      "order_status": 1,
      "pay_data": "https://pay.fast8811.com?o=1610086357457960962&t=8&a=100.00&p=1",
      "order_no": "20230103093050752017",
      "order_time": 1672709455,
      "sign": "c107782502782bf853fa0a3f18e09190"
  },
  "msg": "ok"
}
```
