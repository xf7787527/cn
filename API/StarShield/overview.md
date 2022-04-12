# 京东云星盾OpenAPI接口


## 简介
京东云星盾OpenAPI接口


### 版本
v1


## API
|接口名称|请求方式|功能描述|
|---|---|---|
|**listAvailableCustomPages**|GET|域可以使用的可用自定义页面列表|
|**updateCustomPageURL**|PUT|更新自定义页面URL|
|**createDNSRecord**|POST|创建DNS记录|
|**deleteDNSRecord**|DELETE|删除DNS记录|
|**listDNSRecords**|GET|列出、搜索、排序和筛选域的DNS记录。|
|**updateDNSRecord**|PUT|更新DNS记录|
|**createFilters**|POST|创建新过滤器|
|**createFirewallRules**|POST|创建新的防火墙规则。|
|**deleteIndividualFirewallRules**|DELETE|删除现有防火墙规则。|
|**describeBotStatus**|GET|查询Bot开启状态|
|**listOfFirewallRules**|GET|列出当前定义的所有防火墙规则。|
|**openFirewallBot**|POST|开启BOT|
|**updateIndividualFilter**|PUT|更新一个现有的筛选器。|
|**updateIndividualFirewallRule**|PUT|更新一个单独的现有防火墙规则。|
|**checkInstancesName**|GET|检查实例名称|
|**createFlowPack**|POST|购买流量包|
|**createInstance**|POST|创建套餐实例|
|**describeInstanceByOrderNo**|GET|根据订单号查询套餐实例详情|
|**describeInstances**|GET|套餐实例列表信息查询|
|**describePackage**|GET|套餐包详情查询|
|**describePackages**|GET|套餐包列表查询|
|**modifyInstance**|PUT|升级套餐实例|
|**selectDetailList**|GET|套餐实例续费回调查询|
|**createPageRule**|POST|创建页面规则|
|**deletePageRule**|DELETE|删除页面规则|
|**listAvailablePageRuleSetting**|GET||
|**listPageRules**|GET|获取页面规则列表|
|**updatePageRule**|PUT|替换页面规则。最终规则将与此请求传递的数据完全匹配。|
|**createSSLConfiguration**|POST|上载域的新SSL证书|
|**deleteAdvancedCertificateManagerCertificatePack**|DELETE|对于给定域，删除高级证书包|
|**deleteSSLConfiguration**|DELETE|从域中删除SSL证书。|
|**editSSLConfiguration**|PATCH|上传SSL证书的新私钥和/或PEM/CRT。|
|**editUniversalSSLSettings**|PATCH|修补域的通用SSL设置|
|**listCertificatePacks**|GET|对于给定域，列出所有激活的证书包|
|**listSSLConfigurations**|GET|列出、搜索和筛选所有自定义SSL证书。|
|**orderAdvancedCertificateManagerCertificatePack**|POST|对于一个特定域，订购一个高级证书包|
|**universalSSLSettingsDetails**|GET|获取域的通用SSL证书设置|
|**editFirewallPackage**|PATCH|更改异常检测类型WAF规则包的灵敏度和操作|
|**firewallPackageDetails**|GET|获取有关单个防火墙包的信息|
|**listFirewallPackages**|GET|检索域的防火墙包|
|**listRuleGroups**|GET|搜索、列出和排序包中包含的规则组|
|**listRules**|GET|包内的搜索、排序和筛选规则|
|**ruleGroupDetails**|GET|获取单个规则组|
|**createZone**|POST|创建域|
|**deleteZone**|DELETE|删除存在的域名|
|**listZones**|GET|列出、搜索、排序和筛选您的域|
|**purgeAllFiles**|POST|从星盾的缓存中删除所有文件|
|**purgeFilesByCache_TagsAndHostOrPrefix**|POST|通过指定主机、关联的缓存标记或前缀，从星盾的缓存中精确删除一个或多个文件。<br>注意，缓存标记、主机和前缀清除每24小时的速率限制为30000次清除API调用。一次API调用最多可以清除30个标记、主机或前缀。<br>对于需要以更大容量进行清除的客户，可以提高此速率限制。|
|**purgeFilesByURL**|POST|通过指定URL，从星盾的缓存中细化删除一个或多个文件。<br>要清除带有自定义缓存key的文件，请包括用于计算缓存key的报头。<br>例如要清除缓存key中含有${geo}或${devicetype}的文件，请包括CF-Device-Type或CF-IPCountry报头。<br>注意：当包含源报头时，请确保包括scheme协议和hostname主机名。如果是默认端口，可以省略端口号（http为80，https为443），否则必须包含端口号。|
|**change0_RTTSessionResumptionSetting**|PATCH|开启/关闭 0-RTT|
|**changeAlwaysOnlineSetting**|PATCH|当开启时，在你的源站离线期间，星盾会提供已缓存过的页面。|
|**changeAlwaysUseHTTPSSetting**|PATCH|对所有使用"http"的URL的请求，用301重定向到相应的 "https" URL。如果你只想对一个子集的请求进行重定向，可以考虑创建一个"Always use HTTPS"的页面规则。|
|**changeAutomaticHTTPSRewritesSetting**|PATCH|为该域启用自动HTTPS重写功能。|
|**changeBrotliSetting**|PATCH|当请求资产的客户端支持brotli压缩算法时，星盾将提供资产的brotli压缩版本。|
|**changeBrowserCacheTTLSetting**|PATCH|浏览器缓存TTL（以秒为单位）指定星盾缓存资源将在访问者的计算机上保留多长时间。星盾将遵守服务器指定的任何更长时间。|
|**changeBrowserCheckSetting**|PATCH|浏览器完整性检查与不良行为检查类似，寻找最常被垃圾邮件发送者滥用的常见HTTP头，并拒绝他们访问您的页面。它还会对没有用户代理或非标准用户代理（也是滥用机器人、爬虫或访客常用的）的访客提出挑战质询。|
|**changeCacheLevelSetting**|PATCH|缓存级别的功能是基于设置的级别。<br>basic设置将缓存大多数静态资源（即css、图片和JavaScript）。<br>simplified设置将在提供缓存的资源时忽略查询字符串。<br>aggressive设置将缓存所有的静态资源，包括有查询字符串的资源。|
|**changeChallengeTTLSetting**|PATCH|指定访问者在成功完成一项挑战（如验证码）后允许访问您的网站多长时间。在TTL过期后，访问者将不得不完成新的挑战。我们建议设置为15-45分钟，并将尝试遵守任何超过45分钟的设置。|
|**changeCiphersSetting**|PATCH|一个用于TLS终端的密码允许列表。这些密码必须是BoringSSL的格式。|
|**changeDevelopmentModeSetting**|PATCH|如果你需要对你的网站进行修改，开发模式可以让你暂时进入网站的开发模式。这将绕过星盾的加速缓存，并降低您的网站速度。<br>但如果您正在对可缓存的内容（如图片、css 或 JavaScript）进行更改，并希望立即看到这些更改，这时就很有用。一旦进入，开发模式将持续3小时，然后自动切换关闭。|
|**changeEmailObfuscationSetting**|PATCH|在你的网页上对电子邮件地址进行加密，以防止机器人入侵，同时保持它们对人类可见。|
|**changeEnableErrorPagesOnSetting**|PATCH|星盾将代理源服务器上任何 502、504 错误的客户错误页面，而不是显示默认的星盾错误页面。这不适用于 522 错误，并且仅限于企业级域。|
|**changeEnableQueryStringSortSetting**|PATCH|星盾将把具有相同查询字符串的文件视为缓存中的同一个文件，而不管查询字符串的顺序如何。这只限于企业级域。|
|**changeHotlinkProtectionSetting**|PATCH|启用后，热链路保护选项可确保其他网站无法通过建立使用您网站上托管的图像的页面来占用您的带宽。只要您的网站上的图像请求被星盾选中，我们就会检查以确保这不是其他网站在请求它们。<br>人们仍然能够从你的网页上下载和查看图像，但其他网站将无法窃取它们用于自己的网页。|
|**changeHTTP2EdgePrioritizationSetting**|PATCH|HTTP/2边缘优化，优化了通过HTTP/2提供的资源交付，提高了页面加载性能。当与Worker结合使用时，它还支持对内容交付的精细控制。|
|**changeHTTP2Setting**|PATCH|开启/关闭HTTP2|
|**changeHTTP3Setting**|PATCH|开启/关闭HTTP3|
|**changeIPGeolocationSetting**|PATCH|启用IP地理定位，让星盾对您网站的访问者进行地理定位，并将国家代码传递给您。|
|**changeIPv6Setting**|PATCH|在所有启用星盾的子域上启用 IPv6。|
|**changeMaxUploadSetting**|PATCH|变更上传文件的最大值|
|**changeMinifySetting**|PATCH|为你的网站自动最小化某些资产|
|**changeMinimumTLSVersionSetting**|PATCH|设置HTTPS请求使用的TLS协议的最低版本。例如，如果选择TLS 1.1，那么TLS 1.0连接将被拒绝，而1.1、1.2和1.3（如果启用）将被允许。|
|**changeMirageSetting**|PATCH|自动优化移动设备上网站访问者的图像加载|
|**changeMobileRedirectSetting**|PATCH|自动将移动设备上的访问者重定向到一个移动优化的子域上|
|**changeOpportunisticEncryptionSetting**|PATCH|为当前域启用随机加密|
|**changePolishSetting**|PATCH|剥离元数据并压缩你的图像，以加快页面加载时间。<br>Basic（无损），减少PNG、JPEG和GIF文件的大小 - 对视觉质量没有影响。<br>Basic+JPEG（有损），进一步减少JPEG文件的大小，以加快图像加载。<br>较大的JPEG文件被转换为渐进式图像，首先加载较低分辨率的图像，最后是较高的分辨率版本。<br>不建议用于高像素的摄影网站。|
|**changePrefetchPreloadSetting**|PATCH|星盾将预取包含在响应标头中的任何 URL。这只限于企业级域。|
|**changePrivacyPassSetting**|PATCH|Privacy Pass是一个由Privacy Pass团队开发的浏览器扩展，旨在改善您的访客的浏览体验。启用Privacy Pass将减少显示给你的访客的验证码的数量。|
|**changePseudoIPv4Setting**|PATCH|设置Pseudo IPv4(IPv6到IPv4的转换服务)|
|**changeRocketLoaderSetting**|PATCH|Rocket Loader是一个通用的异步JavaScript优化，它优先渲染你的内容同时异步加载你的网站的Javascript。<br>开启Rocket Loader将立即改善网页的渲染时间，有时以首次绘制时间（TTFP）以及window.onload时间（假设页面上有JavaScript）来衡量，这对你的搜索排名会产生积极影响。<br>当打开时，Rocket Loader将自动推迟加载你的HTML中引用的所有Javascript，而不需要配置。|
|**changeSecurityLevelSetting**|PATCH|为你的网站选择适当的安全配置文件，这将自动调整每个安全设置。如果你选择定制一个单独的安全设置，该配置文件将成为自定义。|
|**changeServerSideExcludeSetting**|PATCH|如果你的网站上有敏感的内容，你想让真正的访问者看到，但你想对可疑的访问者进行隐藏，你所要做的就是用星盾SSE标签来包装这些内容。<br>用下面的SSE标签包住任何你想不让可疑访客看到的内容，<!--sse--><!--/sse-->。<br>例如，<!--sse-->不好的访问者不会看到我的电话号码，555-555-5555<!--/sse-->。注意，SSE只对HTML起作用。<br>如果你启用了HTML最小化功能，当你的HTML源代码通过星盾提供服务时，你不会看到SSE标签。<br>在这种情况下，SSE 仍将发挥作用，因为星盾的 HTML 缩减和 SSE 功能是在资源通过我们的网络传输给我们时即时发生的。当资源通过我们的网络移动到访问者的计算机上时，SSE 仍会发挥作用。|
|**changeSSLSetting**|PATCH|SSL对访问者的连接进行加密，并保护信用卡号码和其他进出网站的个人数据。<br>SSL最多需要5分钟才能完全激活。需要在星盾激活你的根域或www域。<br>Off，访客和星盾之间没有SSL，星盾和你的Web服务器之间也没有SSL（所有HTTP流量）。<br>Flexible, 访客和星盾之间的 SSL -- 访客在你的网站上看到 HTTPS，但星盾和你的 Web 服务器之间没有 SSL。您不需要在您的 Web 服务器上安装 SSL 证书，但您的访客仍会看到启用 HTTPS 的网站。<br>Full, 访客和星盾之间的 SSL -- 访客在你的网站上看到 HTTPS，以及星盾和你的 Web 服务器之间的 SSL。您至少需要有自己的 SSL 证书或自签名的证书。<br>Full (Strict), 访客和星盾之间的 SSL -- 访客在您的网站上看到 HTTPS，以及星盾和您的 Web 服务器之间的 SSL。你需要在你的网络服务器上安装一个有效的SSL证书。<br>这个证书必须由一个证书机构签署，有一个在未来的到期日，并为请求的域名（主机名）作出回应。|
|**changeTLS1_3Setting**|PATCH|为该域启用加密TLS 1.3功能。|
|**changeTLSClientAuthSetting**|PATCH|TLS 客户端授权要求星盾使用客户端证书连接到您的源服务器（Enterprise Only）。|
|**changeTrueClientIPSetting**|PATCH|允许客户继续在我们发送给源的头中使用真正的客户IP。这只限于企业级域。|
|**changeWebApplicationFirewallWAFSetting**|PATCH|WAF检查对您网站的HTTP请求。它检查GET和POST请求，并应用规则来帮助从合法的网站访问者中过滤出非法流量。星盾 WAF 检查网站地址或 URL 以检测任何不正常的东西。<br>如果星盾 WAF确定了可疑的用户行为。那么 WAF 将用一个页面 "挑战 "网络访客，要求他们成功提交验证码以继续其行动。<br>如果挑战失败，行动将被停止。这意味着 星盾 的 WAF 将在任何被识别为非法的流量到达您的源网络服务器之前将其阻止。|
|**changeWebPSetting**|PATCH|当请求图像的客户端支持WebP图像编解码器时。当WebP比原始图像格式具有性能优势时，星盾将提供WebP版本的图像。|
|**changeWebSocketsSetting**|PATCH|WebSockets是客户端和源服务器之间持续的开放连接。在WebSockets连接中，客户端和源服务器可以来回传递数据，而不需要重新建立会话。<br>这使得在WebSockets连接中的数据交换非常快。WebSockets经常被用于实时应用，如即时聊天和游戏。|
|**editZoneSettingsInfo**|PATCH|批量更新域的设置|
|**getAllZoneSettings**|GET|域的相关配置|
|**getAdvancedDDOSSetting**|GET|对您的网站进行高级保护，防止分布式拒绝服务（DDoS）攻击。这是一个不可编辑的值。|
|**getAlwaysOnlineSetting**|GET|获取当前Always Online的配置。当Always Online开启时，在你的源站离线期间，星盾会提供已缓存过的页面。|
|**getAlwaysUseHTTPSSetting**|GET|对所有使用"http"的URL的请求，用301重定向到相应的 "https" URL。如果你只想对一个子集的请求进行重定向，可以考虑创建一个"Always use HTTPS"的页面规则。|
|**getAutomaticHTTPSRewritesSetting**|GET|为该域启用自动HTTPS重写功能。|
|**getBrowserCacheTTLSetting**|GET|浏览器缓存TTL（以秒为单位）指定星盾缓存资源将在访问者的计算机上保留多长时间。星盾将遵守服务器指定的任何更长时间。|
|**getBrowserCheckSetting**|GET|浏览器完整性检查与不良行为检查类似，寻找最常被垃圾邮件发送者滥用的常见HTTP头，并拒绝他们访问您的页面。它还会对没有用户代理或非标准用户代理（也是滥用机器人、爬虫或访客常用的）的访客提出挑战质询。|
|**getCacheLevelSetting**|GET|缓存级别的功能是基于设置的级别。<br>basic设置将缓存大多数静态资源（即css、图片和JavaScript）。<br>simplified设置将在提供缓存的资源时忽略查询字符串。<br>aggressive设置将缓存所有的静态资源，包括有查询字符串的资源。|
|**getChallengeTTLSetting**|GET|指定访问者在成功完成一项挑战（如验证码）后允许访问您的网站多长时间。在TTL过期后，访问者将不得不完成新的挑战。我们建议设置为15-45分钟，并将尝试遵守任何超过45分钟的设置。|
|**getCiphersSetting**|GET|一个用于TLS终端的密码允许列表。这些密码必须是BoringSSL的格式。|
|**getDevelopmentModeSetting**|GET|如果你需要对你的网站进行修改，开发模式可以让你暂时进入网站的开发模式。这将绕过星盾的加速缓存，并降低您的网站速度。<br>但如果您正在对可缓存的内容（如图片、css 或 JavaScript）进行更改，并希望立即看到这些更改，这时就很有用。一旦进入，开发模式将持续3小时，然后自动切换关闭。|
|**getEmailObfuscationSetting**|GET|在你的网页上对电子邮件地址进行加密，以防止机器人入侵，同时保持它们对人类可见。|
|**getEnableErrorPagesOnSetting**|GET|星盾将代理源服务器上任何 502、504 错误的客户错误页面，而不是显示默认的星盾错误页面。这不适用于 522 错误，并且仅限于企业级域。|
|**getEnableQueryStringSortSetting**|GET|星盾将把具有相同查询字符串的文件视为缓存中的同一个文件，而不管查询字符串的顺序如何。这只限于企业级域。|
|**getHotlinkProtectionSetting**|GET|启用后，热链路保护选项可确保其他网站无法通过建立使用您网站上托管的图像的页面来占用您的带宽。只要您的网站上的图像请求被星盾选中，我们就会检查以确保这不是其他网站在请求它们。<br>人们仍然能够从你的网页上下载和查看图像，但其他网站将无法窃取它们用于自己的网页。|
|**getHTTP2EdgePrioritizationSetting**|GET|HTTP/2边缘优化，优化了通过HTTP/2提供的资源交付，提高了页面加载性能。当与Worker结合使用时，它还支持对内容交付的精细控制。|
|**getHTTP2Setting**|GET|获取HTTP2设置的状态|
|**getHTTP3Setting**|GET|获取HTTP3设置的状态|
|**getImageResizingSetting**|GET|图像调整为通过星盾的网络提供的图像提供按需调整、转换和优化。|
|**getIPGeolocationSetting**|GET|启用IP地理定位，让星盾对您网站的访问者进行地理定位，并将国家代码传递给您。|
|**getIPv6Setting**|GET|在所有启用星盾的子域上启用 IPv6。|
|**getMinifySetting**|GET|获取你的网站自动最小化资产的配置|
|**getMinimumTLSVersionSetting**|GET|获取HTTPS请求使用的TLS协议的最低版本。例如，如果选择TLS 1.1，那么TLS 1.0连接将被拒绝，而1.1、1.2和1.3（如果启用）将被允许。|
|**getMirageSetting**|GET|自动优化移动设备上网站访问者的图像加载|
|**getMobileRedirectSetting**|GET|自动将移动设备上的访问者重定向到一个移动优化的子域上|
|**getOpportunisticEncryptionSetting**|GET|获取当前域随机加密设置|
|**getPolishSetting**|GET|剥离元数据并压缩你的图像，以加快页面加载时间。<br>Basic（无损），减少PNG、JPEG和GIF文件的大小 - 对视觉质量没有影响。<br>Basic+JPEG（有损），进一步减少JPEG文件的大小，以加快图像加载。<br>较大的JPEG文件被转换为渐进式图像，首先加载较低分辨率的图像，最后是较高的分辨率版本。<br>不建议用于高像素的摄影网站。|
|**getPrefetchPreloadSetting**|GET|星盾将预取包含在响应标头中的任何 URL。这只限于企业级域。|
|**getPrivacyPassSetting**|GET|Privacy Pass是一个由Privacy Pass团队开发的浏览器扩展，旨在改善您的访客的浏览体验。启用Privacy Pass将减少显示给你的访客的验证码的数量。|
|**getPseudoIPv4Setting**|GET|获取Pseudo IPv4(IPv6到IPv4的转换服务)|
|**getRocketLoaderSetting**|GET|Rocket Loader是一个通用的异步JavaScript优化，它优先渲染你的内容同时异步加载你的网站的Javascript。<br>开启Rocket Loader将立即改善网页的渲染时间，有时以首次绘制时间（TTFP）以及window.onload时间（假设页面上有JavaScript）来衡量，这对你的搜索排名会产生积极影响。<br>当打开时，Rocket Loader将自动推迟加载你的HTML中引用的所有Javascript，而不需要配置。|
|**getSecurityHeaderHSTSSetting**|GET|星盾域的安全标头。|
|**getSecurityLevelSetting**|GET|为你的网站选择适当的安全配置文件，这将自动调整每个安全设置。如果你选择定制一个单独的安全设置，该配置文件将成为自定义。|
|**getServerSideExcludeSetting**|GET|如果你的网站上有敏感的内容，你想让真正的访问者看到，但你想对可疑的访问者进行隐藏，你所要做的就是用星盾SSE标签来包装这些内容。<br>用下面的SSE标签包住任何你想不让可疑访客看到的内容，<!--sse--><!--/sse-->。<br>例如，<!--sse-->不好的访问者不会看到我的电话号码，555-555-5555<!--/sse-->。注意，SSE只对HTML起作用。<br>如果你启用了HTML最小化功能，当你的HTML源代码通过星盾提供服务时，你不会看到SSE标签。<br>在这种情况下，SSE 仍将发挥作用，因为星盾的 HTML 缩减和 SSE 功能是在资源通过我们的网络传输给我们时即时发生的。当资源通过我们的网络移动到访问者的计算机上时，SSE 仍会发挥作用。|
|**getSSLSetting**|GET|SSL对访问者的连接进行加密，并保护信用卡号码和其他进出网站的个人数据。<br>SSL最多需要5分钟才能完全激活。需要在星盾激活你的根域或www域。<br>Off，访客和星盾之间没有SSL，星盾和你的Web服务器之间也没有SSL（所有HTTP流量）。<br>Flexible, 访客和星盾之间的 SSL -- 访客在你的网站上看到 HTTPS，但星盾和你的 Web 服务器之间没有 SSL。您不需要在您的 Web 服务器上安装 SSL 证书，但您的访客仍会看到启用 HTTPS 的网站。<br>Full, 访客和星盾之间的 SSL -- 访客在你的网站上看到 HTTPS，以及星盾和你的 Web 服务器之间的 SSL。您至少需要有自己的 SSL 证书或自签名的证书。<br>Full (Strict), 访客和星盾之间的 SSL -- 访客在您的网站上看到 HTTPS，以及星盾和您的 Web 服务器之间的 SSL。你需要在你的网络服务器上安装一个有效的SSL证书。<br>这个证书必须由一个证书机构签署，有一个在未来的到期日，并为请求的域名（主机名）作出回应。|
|**getTLSClientAuthSetting**|GET|TLS 客户端授权要求星盾使用客户端证书连接到您的源服务器（Enterprise Only）。|
|**getTrueClientIPSetting**|GET|允许客户继续在我们发送给源的头中使用真正的客户IP。这只限于企业级域。|
|**getWebApplicationFirewallWAFSetting**|GET|WAF检查对您网站的HTTP请求。它检查GET和POST请求，并应用规则来帮助从合法的网站访问者中过滤出非法流量。星盾 WAF 检查网站地址或 URL 以检测任何不正常的东西。<br>如果星盾 WAF确定了可疑的用户行为。那么 WAF 将用一个页面 "挑战 "网络访客，要求他们成功提交验证码以继续其行动。<br>如果挑战失败，行动将被停止。这意味着 星盾 的 WAF 将在任何被识别为非法的流量到达您的源网络服务器之前将其阻止。|
|**getWebPSetting**|GET|当请求图像的客户端支持WebP图像编解码器时。当WebP比原始图像格式具有性能优势时，星盾将提供WebP版本的图像。|
|**getWebSocketsSetting**|GET|WebSockets是客户端和源服务器之间持续的开放连接。在WebSockets连接中，客户端和源服务器可以来回传递数据，而不需要重新建立会话。<br>这使得在WebSockets连接中的数据交换非常快。WebSockets经常被用于实时应用，如即时聊天和游戏。|
|**getZoneEnableTLS1_3Setting**|GET|为该域启用加密TLS 1.3功能。|
