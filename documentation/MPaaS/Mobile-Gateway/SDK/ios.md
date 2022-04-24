# 网关-iOS-接入文档

## 1. 系统环境

要求系统环境iOS9.0及以上版本。

## 2. 接入指南
通过类似扩展坞的设计理念，解决了移动SDK适配网关的问题，即所有SDK只需要集成网关SDK即可，无论有多少网关需求，移动SDK均不需要对接适配。

## 3. 集成流程
### 3.1 Pod集成
### 3.1.1 Podfile配置

`source 'http://gitlab.mpaas.jdcloud.com/umapadmin/jdtmpaassdkspecrepo.git'`  
`pod 'JDTGateway', '1.0.0'`   

### 3.1.2 Podspec配置
在使用网关SDK的模块中配置Podspec：

`s.dependency 'JDTGateway'` 
  
`# 网关依赖第三方`  
`s.dependency 'AFNetworking', '~> 3.2.1'`

`# 网关依赖系统库`  
`s.frameworks = 'CoreGraphics','MobileCoreServices','Security','SystemConfiguration'`  

### 3.2 主工程集成

1. 将`JDTGateway.framework`拖入到工程中。
    
2. 在 Link Binary With Libraries 中添加依赖库 `CoreGraphics`, `MobileCoreServices`,`Security`,`SystemConfiguration`。     
    
## 4. 基本功能
### 4.1 网关初始化
初始化网关SDK，网关SDK的APPID和Domain在配置服务时提供，APM，应用发布，H5离线化和热修复均使用网关服务，实现一次初始化即可。

```ObjectiveC
// SDK接入网关需要使用的类
#import <JDTGateway/JDTGateway.h>


// 初始化网关
[JDTAnalyze jdt_initWithDomain:@"服务器的网关地址" handleRequestData:^JDTAnalyzeRequest *(JDTOriResponseData *requestData) {
          
        NSString* timeStamp = [self getTimeStamp];
        NSMutableDictionary* headers = [requestData.headers mutableCopy];
        [headers setValue:timeStamp forKey:@"requestTime"];
        [headers setValue:@"网关ID" forKey:@"jdd-app-id"];
        [headers setValue:@"NONE" forKey:@"jdd-encrypt-type"];
        
        NSString* body = @"";
        if ([requestData.body isKindOfClass:[NSDictionary class]]) {
            NSMutableDictionary* requestDic = [requestData.body mutableCopy];
            body = [self jdmobile_convertNSDictionaryToJsonString:requestDic];
        }
        if ([requestData.body isKindOfClass:[NSData class]]) {
            NSData* data = [requestData.body mutableCopy];
            body = [[ NSString alloc] initWithData:data encoding:NSUTF8StringEncoding];
        }
        
        if ([requestData.body isKindOfClass:[NSString class]]) {
            body = [NSString stringWithFormat:@"data=%@",requestData.body];
        }
        
        JDTAnalyzeRequest* request = [JDTAnalyzeRequest jdt_request];
        request.headers = headers;
        request.body = body;
        return request;
        
      } handleResponseData:^JDTAnalyzeResponse *(JDTOriResponseData *responseData) {
          NSDictionary* body =  responseData.body;
          JDTAnalyzeResponse * response = [JDTAnalyzeResponse jdt_response];
          response.headers = responseData.headers;
          response.body = body;
          return response;
      }];
```

### 4.2 网关SDK网络请求  

```ObjectiveC
// 导入头文件
#import <JDTGateway/JDTGateway.h>

// 发送请求
[[JDTRequestCenter jdt_defaultCenter] jdt_sendRequest:^(JDTRequest * _Nonnull request) {
        // 请求的path
        request.url = @"/upgrade/api/marketRelease/getReleaseData";
        // 请求的headers
        request.headers = @{};
        // 请求的params
        request.parameters = @{};
    } onSuccess:^(NSURLResponse* response, id  _Nullable responseObject) {
        
        NSLog(@"%@ \n%@",((NSHTTPURLResponse*)response).allHeaderFields ,responseObject);
        NSDictionary *dic = [self dictionaryForJsonData:responseObject];
        responseBlock(dic);
    } onFailure:^(NSError * _Nullable error) {
        
    }];
```

## 5.隐私政策合规

为了保证您的App顺利通过检测，结合当前监管关注重点，我们制作了京东SDK初始化合规方案。熟悉监管要求，掌握合规操作流程，拒绝App被下架。

### 合规三步走

##### 1.您需要确保App有《隐私政策》，并且在用户首次启动App时就弹出《隐私政策》取得用户同意。

##### 2.您务必告知用户您选择京东网关SDK服务，请在《隐私政策》中增加如下参考条款：

“我们的产品集成京东网关SDK，京东网关SDK采集设备标识符(IMEI/Mac/device ID/IDFA/OPENUDID/GUID、SIM 卡 IMSI 信息)，用于唯一标识设备，以便为提供网关服务的唯一标识；

##### 3.您务必严格遵守如下初始化步骤，确保用户同意《隐私政策》之后，再初始化京东网关SDK。

【1】在application: didFinishLaunchingWithOptions:函数中加入逻辑判断，用户没有同意《隐私政策》之前，先不调用网关初始化。

【2】确保App首次冷启动时，在用户阅读您的《隐私政策》并取得用户授权之后，才调用正式初始化函数，初始化网关SDK。反之，如果用户不同意《隐私政策》授权，则不能调用初始化函数。

【3】一旦App获取到《隐私政策》的用户授权，后续的App冷启动，开发者应该保证在application: didFinishLaunchingWithOptions:函数中调用预初始化函数(授权后初始化函数必须调用，不能遗漏)。
