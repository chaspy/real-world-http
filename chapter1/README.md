# chapter1

## 1.2 HTTP/0.9でできることを試す

```
$ curl --http1.0 http://localhost:18888/greeting
<html><body>hello</body></html>
```

```
$ curl --http1.0 --get --data-urlencode "search word" http://localhost:18888
<html><body>hello</body></html>
```

## 1.3 HTTP/0.9から1.0への道のり

```
$ curl -v --http1.0 http://localhost:18888/greeting
*   Trying ::1...
* Connected to localhost (::1) port 18888 (#0)
> GET /greeting HTTP/1.0
> Host: localhost:18888
> User-Agent: curl/7.43.0
> Accept: */*
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Thu, 24 May 2018 09:59:35 GMT
< Content-Length: 32
< Content-Type: text/html; charset=utf-8
<
<html><body>hello</body></html>
* Closing connection 0
```

## 1.4 HTTPの先祖（1）電子メール
### 1.4.1 ヘッダーの送信

```
$ curl --http1.0 -H "X-Test: Hello" http://localhost:18888
<html><body>hello</body></html>
```

```
curl -v --http1.0 -A "Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)" http://localhost:18888
* Rebuilt URL to: http://localhost:18888/
*   Trying ::1...
* Connected to localhost (::1) port 18888 (#0)
> GET / HTTP/1.0
> Host: localhost:18888
> User-Agent: Mozilla/5.0 (compatible; MSIE 10.0; Windows NT 6.1; Trident/6.0)
> Accept: */*
>
* HTTP 1.0, assume close after body
< HTTP/1.0 200 OK
< Date: Thu, 24 May 2018 10:08:03 GMT
< Content-Length: 32
< Content-Type: text/html; charset=utf-8
<
<html><body>hello</body></html>
* Closing connection 0
```

## 1.5 HTTPの先祖（2）ニュースグループ

### 1.5.1 メソッド

```
curl --http1.0 -X POST http://localhost:18888/greeting
<html><body>hello</body></html>
```


