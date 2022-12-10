# FUCK-GFW
I do not want waste time in GFW again.
## pip
~/.config/pip/pip.conf
```
[global]
proxy=http://localhost:1087
```
注意不支持socks5
### Reference
* https://my.oschina.net/tangshi/blog/699190

## git
### clone with ssh
在 文件 `~/.ssh/config` 后添加下面两行
```bash
Host github.com
ProxyCommand nc -X 5 -x 127.0.0.1:1080 %h %p
```
### Reference
https://gist.github.com/laispace/666dd7b27e9116faece6

## curl
```bash
socks5 = "127.0.0.1:1080"
```
add to `~/.curlrc`

### Reference
https://www.zhihu.com/question/31360766

## Gradle
这个浪费了好长时间额
~/.gradle/gradle.properties
```
systemProp.http.proxyHost=127.0.0.1
systemProp.http.proxyPort=1087
systemProp.https.proxyHost=127.0.0.1
systemProp.https.proxyPort=1087
```
### Reference
https://stackoverflow.com/questions/5991194/gradle-proxy-configuration

## go get
```
HTTP_PROXY=socks5://localhost:1080 go get
```
测试了下HTTPS_PROXY和ALL_PROXY都不起作用

## npm
```
npm config set proxy http://127.0.0.1:1087
npm config set https-proxy http://127.0.0.1:1087
```
用socks5就报错- -

推荐使用yarn，npm是真的慢

## reference
* https://stackoverflow.com/questions/7559648/is-there-a-way-to-make-npm-install-the-command-to-work-behind-proxy

## gem
~/.gemrc
```
---
# See 'gem help env' for additional options.
http_proxy: http://localhost:1087
```
## reference
* google

## brew
```
ALL_PROXY=socks5://localhost:1080 brew ...
```

## Maven

~/.m2/settings.xml

```xml
<settings>
  ...
  <proxies>
   <proxy>
      <id>example-proxy</id>
      <active>true</active>
      <!-- 代理协议 -->
      <protocol>http</protocol>
      <!-- 代理地址 -->
      <host>proxy.example.com</host>
      <!-- 代理端口 -->
      <port>8080</port>
      <!-- 如果代理不需要登陆，必须删除 username 和 password -->
      <username>proxyuser</username>
      <password>somepassword</password>
      <!-- 不使用代理的站点，可以删除 -->
      <nonProxyHosts>www.google.com|*.example.com</nonProxyHosts>
    </proxy>
  </proxies>
  ...
</settings>
```

### 参考

- <https://maven.apache.org/guides/mini/guide-proxies.html>
- <https://stackoverflow.com/questions/1251192/how-do-i-use-maven-through-a-proxy>