# DNS协议
## DNS协议简介
DNS(Domain Name System)域名系统是互联网的一项服务，他作为一个将域名和IP地址相互映射的一个分布式数据库，能够使人更加方便的访问互联网，DNS使用TCP和UDP端口为53.当前对于每一级域名长度限制为63个字符，域名总长度不超过253个字符。<br/>
## DNS记录类型
常见的记录类型有: 

* 主机记录(A记录):RFC 1035定义，A记录用于名称解析的重要记录，将特定主机名映射到对应主机的IP上。
* 别名记录(CNAME记录)：RFC 1035定义，CNAME记录英语将某个别名指向到某个A记录上，这样就不需要在位某个新名字另外创建一条记录
* IPv6主机记录(AAA记录):RFC 3596定义，与A记录对应，用于将特定的主机名映射到一个主机的IPv6地址
* 服务位置记录（SRV记录）: RFC 2782定义，用于定义提供特定服务的服务器的位置，如主机（hostname），端口（port number）等
* NAPTR记录:RFC 3403定义，它提供了正则表达式方式去映射一个域名。NAPTR记录非常著名的一个应用是用于ENUM查询。

## 软件
* BIND（Berkeley Internet Name Domain），使用最广的DNS<br/>
* DJBDNS（Dan J Bernstein's DNS implementation）<br/>
* MaraDNS<br/>
* Name Server Daemon（Name Server Daemon）<br/>
* PowerDNS<br/>
* Dnsmasq<br/>

## DNS解析过程:
DNS查询有两种方式:递归和轮询。DNS客户端设置使用的DNS服务器一般都是递归服务器，他负责全权处理客户端的DBS查询请求，直到返回最终结果。而DNS服务器之间一般采用迭代查询方式。<br/>
>以查询zh.wikipedia.org为例：<br/>
*客户端发送查询报文"query zh.wikipedia.org"至DNS服务器，DNS服务器首先检查自身缓存，如果存在记录则直接返回结果。<br/>
*如果记录老化或不存在，则
DNS服务器向根域名服务器发送查询报文"query zh.wikipedia.org"，根域名服务器返回.org域的权威域名服务器地址，这一级首先会返回的是顶级域名的权威域名服务器。<br/>
*DNS服务器向.org域的权威域名服务器发送查询报文"query zh.wikipedia.org"，得到.wikipedia.org域的权威域名服务器地址。<br/>
*DNS服务器向.wikipedia.org域的权威域名服务器发送查询报文"query zh.wikipedia.org"，得到主机zh的A记录，存入自身缓存并返回给客户端。<br/>



















##参考
https://zh.wikipedia.org/zh/域名系统