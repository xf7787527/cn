# 网站配置域名、备案和解析


## 操作场景
网站框架构建完成后，需要为网站绑定一个域名，此域名为客户访问网站的入口，当用户需要访问网站时，在浏览器输入网站域名就可以直接进行访问。




## 步骤1： 域名备案和获取授权码

域名需要先完成备案后才能正常使用，如果还没有域名，请先[购买域名](https://net.jdcloud.com)。

京东云提供[备案服务](https://record-console.jdcloud.com)，助力您便捷完成备案，备案授权码在您购买的建站服务控制台获取。

![图片名称](https://img1.jcloudcs.com/image/docs/site-21.png)

购买正式的建站服务1年及以上的版本提供授权码，如果您是试用版，请升级版本后获取授权码。
![图片名称](https://img1.jcloudcs.com/image/docs/site-22.png)



## 步骤2：站点绑定域名


在京美建站控制台，选择购买的站点，单击“后台管理”进入站点编辑页面


![图片名称](https://img1.jcloudcs.com/image/docs/site1203-7.png)


在站点编辑页面，点击后台管理


![图片名称](https://img1.jcloudcs.com/image/docs/site1203-9.png)


选择绑定站点


![图片名称](https://img1.jcloudcs.com/image/docs/site1203-10.png)



输入需要绑定的域名，并添加证书，将证书中的文本内容复制粘贴即可。 


![图片名称](https://img1.jcloudcs.com/image/docs/site1203-3.png)





## 步骤3: 对域名进行解析

通过域名访问某个站点的服务器，必须通过IP地址来实现，域名解析就是将域名重新转换为IP地址的过程。

访问[云解析DNS控制台](https://dns-console.jdcloud.com/list)，先添加域名。在域名列表选择刚添加的域名，点击操作中的解析。

![图片名称](https://img1.jcloudcs.com/image/docs/site0324-2.png)


点击添加解析。

![图片名称](https://img1.jcloudcs.com/image/docs/site0324-3.png)

在添加解析页面，进行解析记录配置。

- 记录类型：选择CNAME解析
- 记录值： 在建站服务中进行获取
- 其它项：可选择默认参数

![图片名称](https://img1.jcloudcs.com/image/docs/site0324-4.png)


查看站点的CNAME解析地址。


![图片名称](https://img1.jcloudcs.com/image/docs/site1203-11.png)





完成以上步骤，在浏览器访问域名后，就可以访问到已经配置好的网站。


