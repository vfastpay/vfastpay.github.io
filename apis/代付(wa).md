# 代付

当前通道：**wa**

| 区域 | 通道（可点击切换）|
| --- |-----------------------------------------------------|
| 巴西 | [iugu](代付.html)|
| 印度 | [dd](代付(dd).html)&nbsp;&nbsp; [wd](代付(wd).html)|
| 菲律宾 | [cs](代付(cs).html)&nbsp;&nbsp; [lf](代付(lf).html) |
| 墨西哥 | [sp](代付(sp).html)|
| 越南 | [ly](代付(ly).html)|
| 印度尼西亚 | [wa](代付(wa).html)|

## 请求地址
https://[[域名]](../help/区域域名.html)/i/transfer/create

## 请求方式
POST

## 请求头
Content-Type:application/json

## 请求参数

| 字段名 | 参数名 | 类型 | 必填 | 示例 | 描述 |
|-----|-----|-----|-----|-----|-----|
|商户号|merchant_code|String|是|100012|商户后台分配的商户号(商户系统->账户信息获取) |
|商户订单号|merchant_order_no|String|是|456545645487|商户系统商户订单号，要求32个字符内 |
|支付通道编码|pay_type|String|是|wab|wab-网银，waw-钱包|
|币种|currency|String|是|INR|卢比|
|电话号码|mobile|String|是|254743123003|收款人联系方式|
|姓名|name|String|是|Jack|银行账户名|
|金额|amount|String|是|100.00|单位(元)，保留两位小数|
|回调地址|notify_url|String|是|https://www.xxx.com/notify|付款成功后支付系统通过该地址通知支付结果|
|下单时间戳|order_time|Number|是|1663402686|精确到秒|
|银行编号|bank_code|String|是|BCA|[银行信息](../help/银行信息.html)|
|银行账号|bank_acount|String|是|56466655|收款银行账号，代付到电子钱包填写手机号码|
|签名|sign|String|是|9a55c3868b414cdc740068420a2d3q00|[签名算法](../rule/签名算法.html)|

## 请求示例

```json
{
  "merchant_code": "100012",
  "merchant_order_no": "20230103113942540675",
  "pay_type": "wab",
  "currency": "IDR",
  "name": "test",
  "mobile": "09456312891",
  "amount": "100.00",
  "notify_url": "https:\/\/www.uwinpay.com\/api\/public\/index.php\/wepay\/pay_notify",
  "order_time": 1672717182,
  "bank_code": "11111",
  "bank_account": "1111222",
  "sign": "18b579bc98d9ebcb67c4c75a84f1bcc6"
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
      "merchant_order_no": "20230103113942540675",
      "amount": "100.00",
      "reality_amount": "100.00",
      "order_status": 0,
      "order_no": "20230103113946061140",
      "order_time": 1672717186,
      "sign": "7a5c05b497e7cdd05fe1630ac967c590"
  },
  "msg": "ok"
}
```
