# Nginx 开启OCSP装订

### OCSP简介

全称为 Online Certificate Status Protocol, 是通用的数字证书在线状态查询协议。大多数客户端、浏览器都会在访问HTTPS网站时查询证书的OCSP状态，以进一步确保访问者的安全性。比如 火狐浏览器\(FireFox\)，就默认校验所有的公开信任证书的OCSP状态。只有通过OCSP校验，FireFox才会正常打开您的网站。

由于 OCSP 校验失败而导致的客户端无法连接情况会有很多，不仅只反应在浏览器端。如果您为移动 APP 的接入使用了双向验证，且每次接入都校验服务器证书的有效性。还比如您为您的 API 服务器接入开启了严格SSL验证模式，即每次对接API时都校验服务器证书的有效性。等等此类环境下，一旦您的客户端网络连接OCSP服务器出现问题，都有可能导致您的服务中断。因为客户端的网络情况是复杂的，多变的，甚至不可预估的。

就最近Let's Encrypt的一个OSCP域名`ocsp.int-x3.letsencrypt.org`被污染，解析到了以31开头的FaceBook的IP或者其他被墙IP，而不是使用Akamai CDN的Let's Encrypt的OSCP服务器上。导致国内的服务器无法正常申请和续期Let's Encrypt的免费证书，以及访问速度变慢。

### 解决因网络问题导致的OCSP校验失败

OCSP装订 可以很好的作为OCSP查询协议的替代方案，也是目前 Mozilla基金会推崇实施的一种在线证书查询协议扩展。它能够利用您的服务器网络为客户端、浏览器提供证书状态查询服务。用户如果能够访问您的网站，就能够通过您的网站服务器查询到证书的状态。因此，为了更好的为您的用户提供加密的网站访问和接入服务，您应该为您的每一个安装SSL证书的服务器开启OCSP装订。

#### Nginx开启OCSP装订

以使用acme.sh申请的Let's Encrypt证书为例，证书会存放在~/.acme.sh/example.com文件夹下，下面有这两个文件：

* fullchain.cer
* example.com.key

编辑Nginx配置文件，在server大括号中加入以下内容：

```text
ssl_certificate /[用户名]/.acme.sh/example.com/fullchain.cer; #证书路径
ssl_certificate_key /[用户名]/.acme.sh/example.com/example.com.key; #私钥路径
ssl_stapling on; #开启OCSP
ssl_stapling_verify on; #开启OCSP验证
ssl_trusted_certificate /[用户名]/.acme.sh/xmgspace.me/fullchain.cer; #证书链路径
```

编辑完成保存之后重启Nginx使其生效。

#### Let's Encrypt补充

另外国内服务器使用Let's Encrypt证书的建议修改hosts以避免DNS污染，国外服务器不需要。在hosts中添加一条`ocsp.int-x3.letsencrypt.org`的记录，将其指向下面其中一个，香港的Akamai CDN，国内访问速度不错：

```text
175.45.42.209
175.45.42.217
```

