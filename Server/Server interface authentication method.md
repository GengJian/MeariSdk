## Server interface authentication method

#### Method

+ when 'signatureVersion=1.0'，use sign authentication method.
+ Use 'userToken/PartnerSecret' as an encrypted private key, do not use as request parameters.
+ The interface is uniformly requested by GET。

#### Parameter

| Parameter Name   | Type   | Instruction                                                  | Required |
| ---------------- | ------ | ------------------------------------------------------------ | -------- |
| signature        | String | Signature result string.                                     | YES      |
| signatureMethod  | String | Signature method, default HMAC-SHA1.                         | YES      |
| timestamp        | String | UTC time. The format is YYYY-MM-DDThh:mm:ssZ.                | YES      |
| signatureVersion | String | Signature algorithm version. The default is 1.0.             | YES      |
| signatureNonce   | String | Unique random number, timestamp. Users need to use different random values in different requests | YES      |

*signature For example*

```
signature = Base64.encode(HmacSha1("appVer=3.1.0&appVerCode=95&lngType=zh&phoneType=a&signatureMethod=HMAC-SHA1&signatureNonce=1&signatureVersion=1.0&sourceApp=8&timestamp=1&userID=100000000046", userToken/PartnerSecret))
```

> The parameters should be spliced in lexicographic order