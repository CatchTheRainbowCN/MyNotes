# http请求

```java
HttpHeaders header = new HttpHeaders();
String token =  'token';
Hearder.set("auther", token);
String content = JSON.toJSONString(postParam);
HttpEntity<String> request = new HttpEntity(conent, headers);
String url = "https//localhost:8080";
ResponseEntity<String> postForEntity = restTemplate.postForEntity(url, request, String.class);
String body = postForEntity.getBody();
```

```java
HttpHeaders header = new HttpHeaders();
String token =  'token';
Hearder.set("auther", token);
HttpEntity<String> request = new HttpEntity(null, headers);
MultiValueMap<String, String> params = new LinkedMultiValueMap<>();
params.add("paramName1", "paramValue1");
params.add("paramName2", "paramValue2");
String url = "https//localhost:8080";
UriComponentsBuilder builder = UriComponentsBuilder.fromHttpUrl(url);
URI uri = builder.queryParams(params).build().encode().toUri();
ResponseEntity<String> exchange = restTemplate.exchange(uri.toString, HttpMethod.GET, request, String.class);
String body = exchange.getBody();
```

```java
URI uri = UriComponentsBuilder.fromHttpUrl(url + "/{currentPage}/{pageSize}").queryParam("id", "{id}")
.encode()
.buildAndExpand(currentPage, pageSize, id)
.toUri();
DefaultUriBuilderFactory factory = new DefaultUriBuilderFactory("url");
factory.setEncodingMode(DefaultUriBuilderFactory.EncodingMode.TEMPLATE_AND_VALUES);
restTemplate.setUriTemplateHandler(factory);
HttpHeaders header = new HttpHeaders();
String token =  'token';
Hearder.set("auther", token);
HttpEntity<String> request = new HttpEntity(null, headers);
ResponseEntity<String> exchange = restTemplate.exchange(uri, HttpMerhod.GET, request, String.class);
String body = exchange.getBody();
```
