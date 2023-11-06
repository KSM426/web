전체 코드
```javascript
var http = require('http');
var fs = require('fs');
var url = require('url');
 
var app = http.createServer(function(request,response){
    var _url = request.url;
    console.log(_url);
    var queryData = url.parse(_url, true).query;
    console.log(queryData.id);
    if(_url == '/'){
      _url = '/index.html';
    }
    if(_url == '/favicon.ico'){
      return response.writeHead(404);
    }
    response.writeHead(200);
    response.end(queryData.id);
 
});
app.listen(3000);
```
***
url 모듈
+ url 정보를 받아오기 위한 모듈
```javascript
var url = require('url');
```

+ url의 정보를 문자열로 전달
```javascript
var _url = request.url;
```

+ 문자열 데이터를 url 객체로 변환
```javascript
var queryData = url.parse(_url, true).query;
```
+ parseQueryString	 
+ true : 객체로 변환
+ false : 문자열로 변환

Url 객체 구조
```javascript
var _url = request.url;
var queryData = url.parse(_url, false);
console.log(queryData);
```
출력 결과
```
Url {
  protocol: null,
  slashes: null,
  auth: null,
  host: null,
  port: null,
  hostname: null,
  hash: null,
  search: '?id=HTML',
  query: 'id=HTML',
  pathname: '/',
  path: '/?id=HTML',
  href: '/?id=HTML'
}
```

```javascript
var _url = request.url;
var queryData = url.parse(_url, true).query;    console.log(queryData);
```
출력 결과
```
[Object: null prototype] { id: 'HTML' }
```