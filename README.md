



## 0x01 获取真实ip地址 api.ip.sb

```
GET /jsonip?callback=jsonp_callback_随机字母 HTTP/1.1
Host: api.ip.sb
Accept: */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Connection: close


HTTP/1.1 200 OK
Server: nginx
Content-Type: application/json; charset=utf-8
Connection: close
Vary: Accept-Encoding
Content-Length: 50

jsonp_callback_随机字母({"ip":"外网ip地址"});
```

`honey/format/js/portrait.js`

```
        function o() {
            return n.default.jsonpGetJSON("https://api.ip.sb/jsonip", "callback")
        }

```
## 0x02 rsa 传输敏感信息

`honey/format/js/portrait.js`

```
        function w(r) {
            var n = g(r), t = new Array(n), i = 0;
            for (var o in r) t[i] = o, i += 1;
            t.sort();
            for (var a = new Array(n), u = 0; u < n; u++) a[u] = t[u] + "==" + (0, e.default)(r[t[u]]);
            var s = l.Base64.encode(a.join("&&"));
            return new c.default("-----BEGIN RSA PUBLIC KEY-----\nMIIBCgKCAQEAoFFaYiUG8Koc05H85I2w3zwQekOLg8aPfjPxBMJhWxCVjau8wiek\nmo9jgWEjrDui8tlQSKZT006boe2BksLeOeQFnJMfoYtBbF9x8n8kXykUS+8CWY9V\nEFd/yK3GMrfqo58+ov0Y4QN3ln7Bfwn/52pSbf16R9IXuEaY7pHydPNA1B48t7tA\nNRO4BHqpcCbVtgQu1haHJRhP+3ID1oHHDKNRh5DjwU+Ls6zhfRhB/O77QkhDotx2\nhCKm43/4SPenL8TWJAQS9iAH8HDTEGsy23+TGn729KaMymJf3ZRAr3Gyo22+qtGv\nrMgcVHM2iBGLtRvxY9sTIWY0Vzy3dwSYfwIDAQAB\n-----END RSA PUBLIC KEY-----", "pkcs1-public-pem", {encryptionScheme: "pkcs1"}).encrypt(s, "base64", "utf8")
        }

        function v(e) {
            window.result = e;
            var r = document.location, n = "";
            if ("string" == typeof window.server && 0 !== window.server.length) {
                var t = document.getElementById("err_img"), i = document.createElement("img");
                i.src = window.server + "/src/344.gif?params=" + e.portrait_sign, t.appendChild(i)
            } else n = r.origin + "/api/portrait";
            u.default.post(n, e).catch(function (e) {
                return e
            })
        }
```

## api/portrait

`/src/344.gif?params=`

```
POST /api/portrait HTTP/1.1
Accept: application/json, text/plain, */*
Accept-Language: zh-CN,zh;q=0.8,en-US;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Content-Type: application/json;charset=utf-8
Content-Length: 1728
Connection: close

{"portrait_sign":"GDGk5/JMdBSvxt4GeVLezAOSQduOoTMZXEbSTCGY5Eh6GYcb18CmcJVhvbS5ZUFnQ9iIHAKkTs2UQhtsKSwAPsWksofHkkszB3bHvDv67yvm4HUMWqUVtmF+vxV75MI/86GPV6ShXj8V9EGmPl3DGSUIFt8ChYxxUIJjFLJoDA+0qyJEGzNQ2JL3e9zoM81iaVmpSrS44HYNvNY9ejhdFkSvB/eq/hHijOKXfH7sOI+lazq1e43GsXZvCFPaf4cWRu7l33CvFeoerXAE01Y5uIwPalMdAsV8339lt5W6IpNvvkqPLcm5SwCtWYxkynxuN4Yd9nHaFG9AvHQaQ3zH81iOFWxOwDwkfTxZClLgsL9Py1h+GwiGYDJqQxuPoRUdHnS821htm+vTps+joFmp3xmferJsBSvuhgNJadXKoGvn9L99dnl6dmBD/MKexeS8E024xsGbprjPeyYM5s0C79buW11fzBq7E/p3StTA8SOzgXA3zo/AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA/wEVtaEyT6MGexhAZR68vFmju+DsujbLJoX0x5d0uo6qgCMsy+tmRIyJH8mkTiv4Ir80jRpfjtDOj5yKWYMp4ZD3mf9Bo2peBAwEWpmmsuGnsuZ+NC96KrA0tHZCC8E2xcXXG/pGHGSbKHEld2fKsb4FY+nLA9gl3X6H31esvIbm1+tdpRbDgfZpXCu0J6cQVJ1A5gR9WFdS2euXodOXmzm+OSHbRHWxAM0FTnQAkOsktxazlfk93kr+D0xHFzzX/GNyuJlmMdn8Fo662I0Z4oEdOqb8MOwHO6O16tQFOmw463T9tC5BkV6h98yIsqyu5SznwoXSfy0yZ7rmrVasg5bqBIf8kRc2KR1MIRaxqSQLDJ0B3GGDwJdpjGZOiTuzjQFStwA0GgRuk+DXllSWFW782G5E2+m5F4TRsBMDmnRZn7tXDh5p93ZutKJXc3hMnAeXGmawYD6waE/Oh3ajzquHfKnQD6Tg/LUzoXFV4/yq9pU++navi2c2R+eRLcx0+jAZ9eUkKS1rlMEkALGNa0rjjrxbk2aYI5X/3CL15dc7wnRSeHH2EWGdNgaaqqOSvzskdN55CVYyxCrtOEYvaH2OOijKesXezkKemRlFphShZhk5442oxJ9/cGTHZ4Jl9URgYGznpREHemyBXEEX7yAF4jRw/4RDviakxfyudoEjmpmIqGt+yjIysFPAFgeZXgvtt89SkG8kRBbs/gmQp5JFOSA+vRKocfvdRFQO4aB0C5Odc2RoVwdzOEXubE0HTgFDCWuZOjMzT1sC+29jTdtgOONeXK8sUsTukvDMxC46dnPgNleDxOFkyV0N8finZtGjja0RHGK+oupjJLLjpVcWeO7YFvJZxAZxX6e1sHGLnd64U4hPNok6Mm7fqezmn7DkShP30FIhuynL8DQb9wopEISEOkxprHEdIz0truoIjZTfbdTcvZFw5X2whm7myhFl7wA4Ou8j0uGCW1XwUgHcXHm5vLkuovKRefDwoOu684vWZAo="}

HTTP/1.1 200 OK
Server: gunicorn/20.0.4
Connection: close
Content-Type: text/html; charset=utf-8
Content-Length: 2
Access-Control-Allow-Origin: *
Access-Control-Allow-Methods: GET, POST, OPTIONS
Access-Control-Allow-Headers: content-type
Referrer-Policy: no-referrer

ok
```

```
        function v(e) {
            window.result = e;
            var r = document.location, n = "";
            if ("string" == typeof window.server && 0 !== window.server.length) {
                var t = document.getElementById("err_img"), i = document.createElement("img");
                i.src = window.server + "/src/344.gif?params=" + e.portrait_sign, t.appendChild(i)
            } else n = r.origin + "/api/portrait";
            u.default.post(n, e).catch(function (e) {
                return e
            })
        }
```
## 解密加密数据

browser
host
network
social
```


browser==
{"name":"chrome","version":"84.0.4147","versionNumber":84.04147,"mobile":false,"os":"OS X 10.15.5","canvasFingerprint":"xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"}
{
  "name": "chrome",
  "version": "84.0.4147",
  "versionNumber": 84.04147,
  "mobile": false,
  "os": "OS X 10.15.5",
  "canvasFingerprint": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
}
&&host=={"cpuConcurrency":6,"fonts":["Andale Mono","Arial","Arial Black","Arial Hebrew","Arial Narrow","Arial Rounded MT Bold","Arial Unicode MS","Comic Sans MS","Courier","Courier New","Geneva","Georgia","Helvetica","Helvetica Neue","Impact","LUCIDA GRANDE","Microsoft Sans Serif","Monaco","Palatino","Tahoma","Times","Times New Roman","Trebuchet MS","Verdana","Wingdings","Wingdings 2","Wingdings 3"],"timezone":"Asia/Shanghai","language":"zh-CN","screenResolution":[1792,1120],"render":"ATI Technologies Inc.~AMD Radeon Pro 5300M OpenGL Engine","os":"OS X 10.15.5","touchSupport":false,"hasUnity":false}
{
  "cpuConcurrency": 6,
  "fonts": [
    "Andale Mono",
    "Arial",
    "Arial Black",
    "Arial Hebrew",
    "Arial Narrow",
    "Arial Rounded MT Bold",
    "Arial Unicode MS",
    "Comic Sans MS",
    "Courier",
    "Courier New",
    "Geneva",
    "Georgia",
    "Helvetica",
    "Helvetica Neue",
    "Impact",
    "LUCIDA GRANDE",
    "Microsoft Sans Serif",
    "Monaco",
    "Palatino",
    "Tahoma",
    "Times",
    "Times New Roman",
    "Trebuchet MS",
    "Verdana",
    "Wingdings",
    "Wingdings 2",
    "Wingdings 3"
  ],
  "timezone": "Asia/Shanghai", // 地区
  "language": "zh-CN",
  "screenResolution": [
    1792,
    1120
  ],
  "render": "ATI Technologies Inc.~AMD Radeon Pro xxxxM OpenGL Engine", //图形卡
  "os": "OS X 10.15.5", // 系统OS
  "touchSupport": false,  
  "hasUnity": false
}
&&network=={"externalIP":{"ip":"x.x.x.x"},"realIP":{"ip":"x.x.x.x"},"internalIP":{}}
{
  "externalIP": {
    "ip": "x.x.x.x"
  },
  "realIP": {
    "ip": "x.x.x.x"
  },
  "internalIP": {}
}
&&social=={}

```

# 背景
在真实攻防演习中，蓝队不再像以前只是被动防守，而是慢慢开始转变到主动出击的角色。对蓝队反制红队帮助最大的想来非蜜罐莫属，现在的商业蜜罐除了会模拟一个虚拟的靶机之外，还承担了一个很重要的任务：溯源黑客真实身份。相当一部分黑客因为浏览器没开隐身模式导致被利用jsonhijack漏洞抓到真实ID，虽然可以反手一个举报到src换积分，但是在漏洞修复之前，又是一批战友被溯源。相信很对已经被溯源的红方选手对此更有体会。
在这种背景下，各位红方老司机应当很需要一个能自动识别这种WEB蜜罐，因此我们写了个简单的chrome插件，用来帮助我们摆脱被溯源到真实ID的困境。插件有两个功能，一是识别当前访问的网站是否是蜜罐，是的话就弹框预警；二是对访问的jsonp接口进行重置，防止对方获取到真实ID。所采用的原理非常简单粗暴，就是判断当前网站域和jsonp接口的域是否是同一个，是的话就预警并阻断。比如我访问一个
`http://1.2.3.4/` 的网站，结果这个网站里的js去请求了一个baidu.com的api，那妥妥的有问题了。但是粗暴判断也会带来误报，比如我正常访问baidu.com，但是其引用了个apibaidu.com的jsonp，就一样也会报警和拦截，这种情况下就暂时用白名单来解决了。

# 使用
打开chrome的插件管理 chrome://extensions/。
打开开发者模式，并点击”加载已解压的扩展程序”，选择对应的目录导入即可
