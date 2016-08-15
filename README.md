# wxsign
微信自定义分享的签名版golang后端实现，自带ticket暂存机制

## 安装
```
go get github.com/EagleChen/wxsign
```

## 用法
```
appID := "aaa" // 微信公众号的appid 和 密钥
secret   := "bbb"
url := "www.qq.com" // 要分享的URL
signer := wxsign.NewSigner(appID, secret)
resp, _ := signer.GenSignature(url)
fmt.Printf("%+v\n", resp)
```
输出类似结果:
```
{NonceStr:A9FpXzp1LGIehp1b Timestamp:1470249579 Signature:cb8433318a68f76c381be2a1f277f2d337b41dfb}
```

## 说明
根据微信[官方文档](http://mp.weixin.qq.com/wiki/7/aaa137b55fb2e0456bf8dd9148dd613f.html)，token和ticket需要缓存在客户端，不要每次生成签名都请求新的。这个缓存机制已经实现。
