# CDN

CDN就是内容分部网络（Content Delivery Network），它是构筑在现有Internet上的一种先进的流量分配网络。其目的是在现有的Internet中增加一层新的网络架构，利用最靠近每位用户的服务器，将网站的内容发布到最接近用户的网络“边缘”，使用户可以就近取得所需内容，**提高用户访问网站的响应速度**。

有别于镜像，CDN比镜像更智能
CDN = 镜像(Mirror) + 缓存(Cache) + 整体负载均衡(GSLB)

目前CDN都以缓存网站中的静态数据为主，如css、js、图片和静态页面等数据。用户在从主站服务器请求到动态内容后再从CDN上下载这些静态数据，从而加速网页数据内容的下载速度。

通常来说CDN要达到以下几个目标

- 可扩展(Scalability)
- 安全性(Security)
- 可靠性、响应和执行(Reliability、Responsiveness and Performance)

## CDN架构

![cdn架构](http://image.webreader.duokan.com/mfsv2/download/s010/p0115k6wPIYG/bhs005bMb5wC5P.jpg)

如图所示，一个用户访问某个静态文件，首先要向LDNS服务器发起请求，一般经过迭代解析后回到这个域名的注册服务器去解析，一般每个公司都有一个DNS解析服务器。这是，这个DNS解析服务器通常会把它重新CNAME解析到另外一个域名，而这个域名最终会被指向CDN全局中的DNS负载均衡服务器，再由这个GTM来最终分配是那个地方的访问用户，返回给离这个访问用户最近的CDN节点。

## 负载均衡

Load Balance就是对工作任务进行平衡、分摊到多个操作单元上执行，共同完成操作任务。

通常有三种负载均衡架构

### 链路负载均衡

![链路负载均衡](http://image.webreader.duokan.com/mfsv2/download/s010/p013zjFXwpgw/OO9qjVesBvruOM.jpg)

通过DNS解析成不同的IP，然后用户根据这个IP来访问不同的目标服务器，即最终访问那个Web Server是由DNS Server来控制的。

### 集群负载均衡

#### 硬件负载均衡

![硬件负载均衡](http://image.webreader.duokan.com/mfsv2/download/s010/p01oxTrM6S2O/wtoJfWot5sxsNH.jpg)

使用昂贵的专门硬件设备来转发请求，性能好，但是当访问量陡然增大时，不能进行动态扩容。

#### 软件负载均衡

使用普遍的负载方式，成本低廉。一次访问请求要经过多次代理服务器，会增加网络延时。

![软件负载均衡](http://image.webreader.duokan.com/mfsv2/download/s010/p01dYhQjNP8K/WxVvcW6mwdS4Zy.jpg)

上面两台是LVS，使用四层负载均衡，也就是在网络层利用IP地址进行地址转发。下面三台使用HAProxy进行七层负载，也就是可以根据访问用户的HTTP请求头来进行负载均衡

### 操作系统负载均衡

利用操作系统级别中的软中断或者硬件中断来达到负载均衡。



























