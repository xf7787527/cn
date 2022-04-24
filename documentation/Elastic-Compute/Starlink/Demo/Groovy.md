# Groovy示例
 演示了Groovy语言下各种触发器、连接器、函数的示例配置、用法和代码，示例代码可访问： [groovy-demo](https://starlink-console.jdcloud.com/studio/v2/index.html#/?vms=eyJ2bXNLZXkiOiJlMTE2NzcwMzgwNzQ0ZTNmOTU1NjM5ZGNmZjRiOTU0YSIsInZtc05hbWUiOiJncm9vdnktZGVtbyIsImdpdFVybCI6Imh0dHBzOi8vY29kZS5qZGNsb3VkLmNvbS9zdGFybGluay12bXMvZ3Jvb3Z5LWRlbW8uZ2l0Iiwic2NyaXB0VHlwZSI6Ikdyb292eSIsInRlYW1LZXkiOiIzMDFiMzFjMjVkZjI0YzQ2YjI2N2MwZGUzODMzMGU2YSIsImdyb3VwSWQiOiJjb20uamQuZGVtbyIsImF1dGhDb2RlIjowLCJ0ZWFtTmFtZSI6ImRlbW8ifQ)。
 
> 示例VMS可以查看，但不可以修改/部署，您可以克隆至您自己的团队内修改。

## Connector 连接器配置
### Http Connector 连接器配置
**配置：**
#### 新建连接器
输入 **连接器名称** 和选择 **连接器类型** 为HTTP
![新建http连接器](../../../../image/Starlink/Demo/新建httpConnector.png)
#### 基础配置
- 1、点击连接器基础信息
- 2、配置连接器基础信息 **摘要** 和 **描述**
- 3、配置连接器配置信息 **根URL(支持环境变量配置)** **连接超时时间** **读写超时时间** **最大并发请求数**
    ![配置http连接器基本信息](../../../../image/Starlink/Demo/配置http连接器基础信息.png)
#### 新增http连接器方法
- 1、支持 **get**、**post**、**put**、**delete** 请求类型
- 2、输入 **名称** **路径** **类型**
  ![新增http方法](../../../../image/Starlink/Demo/新增http方法.png)
#### 配置http方法信息
- 1、配置基础信息
    ![配置http方法基础信息](../../../../image/Starlink/Demo/配置http方法基础信息.png)
- 2、配置方法定义
    - 1、配置 **URL查询参数**
        URL 查询参数 即 url 后以 **&** 符号拼接参数 例如 id=1&name=zhangsan
        ![配置http方法URL查询参数](../../../../image/Starlink/Demo/配置http方法URL查询参数.png)
    - 2、配置 **URL路径参数**
        URL 路径参数 即 以 {name} 在路径定义的参数
         ![配置http方法URL路径参数](../../../../image/Starlink/Demo/配置http方法URL路径参数.png)
    - 3、配置 **请求头参数**
        请求头参数 即 http 请求需要的 请求头数据
        ![配置http方法请求头参数](../../../../image/Starlink/Demo/配置http方法请求头参数.png)
    - 4、配置 **Cookie参数**
        Cookie 多个参数以 ; 拼接, 拼接参数 以 Cookie 放入请求头
        ![配置http方法Cookie参数](../../../../image/Starlink/Demo/配置http方法Cookie参数.png)
    - 5、配置 **请求体**
        配置请求体数据 请求类型 支持 **json、text、x-www-form-urlencoded**
        ![配置http方法请求体数据](../../../../image/Starlink/Demo/配置http方法请求体数据.png)
    - 6、请求参数和示例值互转
        为方便请求参数配置，支持参数定义与示例值互转，示例值有固定的结构，query表示url请求参数，path表示url请求路径参数，header表示请求头参数，body表示请求体参数，cookie表示cookie 参数。
        ![http方法请求参数与示例值互转](../../../../image/Starlink/Demo/http方法请求参数与示例值互转.png)
- 3、配置响应参数
    - 1、配置响应体
        选择响应体根类型     
        ![配置响应体参数](../../../../image/Starlink/Demo/配置http方法响应体参数.png)
    - 2、配置响应头
        配置响应头参数     
         ![配置http方法响应头参数](../../../../image/Starlink/Demo/配置http方法响应头参数.png)
    - 3、响应参数和示例值互转
        为方便响应参数定义，支持响应参数与响应示例值互转![http方法响应参数与示例值互转](../../../../image/Starlink/Demo/http方法响应参数与示例值互转.png)
### 数据源配置
**配置：**
#### 新建数据源
  目前只支持 **mysql** 类型数据源
  ![新建数据源](../../../../image/Starlink/Demo/新建数据源.png)

#### 配置数据源
**jdbcUrl 用户名 密码** 支持环境变量配置， 其他参数有默认值，可以根据实际需求进行调整
![配置数据源](../../../../image/Starlink/Demo/配置数据源.png)
### DB 连接器配置
**配置：**
#### 新建连接器
输入 **连接器名称** 和选择 **连接器类型** 为DB
![新建DB连接器](../../../../image/Starlink/Demo/新建DB连接器.png)
#### 基础配置
- 1、点击连接器基础信息
- 2、配置连接器基础信息 **摘要** 和 **描述**
- 3、配置连接器配置信息 **数据源(选择数据源绑定)**
  ![配置db连接器基础信息](../../../../image/Starlink/Demo/配置db连接器基础信息.png)
#### 新增DB连接器方法
- 1、支持 **select**、**update**、**delete**、**insert** 类型
- 2、输入 **名称** **类型**
  ![新增DB方法](../../../../image/Starlink/Demo/新增DB方法.png)
#### 配置DB方法信息
- 1、配置基础信息
  ![配置DB方法基础信息](../../../../image/Starlink/Demo/配置DB方法基础信息.png)
- 2、配置方法定义
    - 1、**MyBatis Mapper语句**
        MyBatis Mapper语句 依据mybatis sql 语法， 不支持返回类型为自定义对象
        ![配置DB方法mapper信息](../../../../image/Starlink/Demo/配置DB方法mapper信息.png)
    - 2、配置 **请求参数和响应参数**
        请求参数点击 添加参数 对应 mapper 语句的变量， 选择返回参数类型
        ![配置DB方法请求参数和响应参数](../../../../image/Starlink/Demo/配置DB方法请求参数和响应参数.png)
    - 3、请求参数和示例值互转
        方便参数定义，支持示例值转定义参数
        ![DB方法请求参数与示例值互转](../../../../image/Starlink/Demo/DB方法请求参数与示例值互转.png)
    - 4、响应参数和示例值互转
        方便参数定义，当返回是object 或者 list 类型支持相应参数与响应示例值互转
        ![DB方法相应参数与示例值互转](../../../../image/Starlink/Demo/DB方法相应参数与示例值互转.png)
## Function 函数配置
### Groovy 函数配置
**配置：**
#### 新建Groovy类型函数
填入 函数名称(不可与其他函数重名) 选择 函数类型 Groovy
![新建groovy函数](../../../../image/Starlink/Demo/新建groovy函数.png)
#### 编辑开发Groovy类型函数
创建函数之后就可以在该函数中写我们的业务逻辑了，面板分三块， 入参 出参 工作区 （如有入参和出参请一定定义参数）
![编辑groovy函数](../../../../image/Starlink/Demo/编辑groovy函数.png)
#### 常用api示例用法
```Groovy
import com.jd.starlink.engine.sdk.log.*;
import com.jd.starlink.engine.sdk.json.JsonUtil;
import com.jd.starlink.engine.sdk.annotation.Inject;
import com.jd.starlink.engine.sdk.function.Function;
import com.jd.starlink.engine.sdk.connector.DBConnector;
import com.jd.starlink.engine.sdk.connector.RpcConnector;

/**
 * 处理具体逻辑的 groovy 类型 函数 示例 （常用工具及代码示例）
 */
public class HandleBussinessGroovy{

    /**
     * 声明LOG，注意使用无参的方法获取Logger对象，通过这种方式的Logger对象不能在线程池中使用
     */
    private final Logger log = LoggerFactory.getLogger();

    /**
     * 如果在线程池中使用，需要使用有参的方法获取Logger对象，入参为VMS名称，而不是当前的类名
     */
    private final Logger log2 = LoggerFactory.getLogger("groovy-demo");

    /**
     * 通过 Inject 注解注入函数对象(可以注入代码函数或者bpmn函数)
     */
    @Inject
    private Function handleBussinessGroovy;

    /**
     * Inject注解也支持通过name来指定DB连接器的名称
     */
    @Inject
    private DBConnector mysqlConnector;

    /**
     * Inject注解也支持通过name来指定HTTP连接器的名称
     */
    @Inject
    private RpcConnector juheGoodBook;

    Map doCall (Map map) {

        // 日志使用
        log.info("hello world");
        log.info("hello world mes:{}", "aaa");
        log.debug("hello world");
        log.debug("hello world mes:{}", "aaa");
        log.warn("hello world");
        log.warn("hello world mes:{}", "aaa");
        log.error("hello world");
        log.error("hello world mes:{}", "aaa");

        // json工具使用
        // toJson
        User user = new User();
        user.setName("zhangsan");
        user.setId("00001");
        String toJson = JsonUtil.toJson(user);
        // fromJson
        User fromJson = JsonUtil.fromJson(toJson, User.class);

        // 调用 function 函数
        Map<String,Object> funcParamsMap = new HashMap<>();
        funcParamsMap.put("param1", "aaa");
        funcParamsMap.put("param2", "bbb");
        Map<String, Object> funcResultMap = (Map<String, Object>)handleBussinessGroovy.invoke(funcParamsMap);

        // 调用db连接器
        int count = mysqlConnector.invoke("selectCount");
        Map<String,Object> addUserMap = new HashMap<String,Object>();
        addUserMap.put("pin", "0");
        addUserMap.put("realName", "zhangshan");
        addUserMap.put("idType", "0");
        addUserMap.put("idNo", "00001123");
        addUserMap.put("mobile", "1888888777");
        addUserMap.put("status", "1");
        int addRes = mysqlConnector.invoke("addUser", addUserMap);

        // 调用HTTP连接器 可以设置 query,path, header, cookie,body  等参数  注意 map 的 key 必须以这几个为key
        Map<String,Object> methodParamsMap = new HashMap<String,Object>();
        // 设置 query url 参数
        Map<String,Object> query = new HashMap<String,Object>();
        query.put("key", "08e92ae4949756ba4fdef17f2a78b29f");
        query.put("dtype", "json");
        methodParamsMap.put("query", query);
        Map<String, Object> result = (Map<String, Object>)juheGoodBook.invoke("catalog", methodParamsMap);
        // 获取响应体
        Map<String, Object> resultBody = (Map<String, Object>)result.get("body");
        // 获取响应头
        Map<String, Object> resultHeaders = (Map<String, Object>)result.get("headers");

        return ["data":resultBody]
    }
}
class User{
    public String id;
    public String name;

    public String getId() {
        return id;
    }

    public void setId(String id) {
        this.id = id;
    }

    public String getName() {
        return name;
    }

    public void setName(String name) {
        this.name = name;
    }
}
```
### bpmn 函数配置
**配置：**
#### 新建bpmn类型函数
  点击新增函数，填入 **函数名称** 选择 **函数类型** BPMN
  ![新建bpmn函数](../../../../image/Starlink/Demo/新建bpmn函数.png)
#### 配置bpmn函数
- 1、编辑函数的入参和出参
    根据自己的业务编辑 bpmn 的入参和出参
    ![编辑bpmn函数的入参和出参](../../../../image/Starlink/Demo/编辑bpmn函数的入参和出参.png)
- 2、拖入任务处理模块。任务分 服务任务 函数任务
    根据业务需求绑定自己需要的任务类型
    ![增加bpmn业务处理模块](../../../../image/Starlink/Demo/增加bpmn业务处理模块.png)
    - 服务任务类型 （支持直接调用 连接器 HTTP DB）
        绑定 HTTP 连接器 并 绑定 连接器入参 （别名整个bpmn函数唯一）
        ![配置bpmn服务任务HTTP](../../../../image/Starlink/Demo/配置bpmn服务任务HTTP.png)
        绑定 DB 连接器 并 绑定 连接器入参 （别名整个bpmn函数唯一）
        ![配置bpmn服务任务DB](../../../../image/Starlink/Demo/配置bpmn服务任务DB.png)
    - 函数任务类型 （支持调用其他函数 包括 JavaScript类型函数 或者 bpmn 函数）
        绑定对应函数 并 绑定 函数入参 （别名整个bpmn函数唯一）
        ![配置bpmn函数任务](../../../../image/Starlink/Demo/配置bpmn函数任务.png)
## Trigger 触发器配置
### kafka 触发器配置
#### 新建kafka消费者触发器
输入 触发器名称 选择 触发器类型 KAFKA 绑定 **函数**`（函数入参类型必须是 message -  Object, 函数可以是 Groovy 函数 也可以是 bpmn 函数）`
![新建kafka消费者触发器](../../../../image/Starlink/Demo/新建kafka消费者触发器.png)
#### 编辑kafka消费者触发器
填写 **摘要** **kafka接入点**(接入kafka集群地址，以逗号分隔，可以引用环境变量) **主题** **分组** **每次拉去最大条数** **最大阻塞时间(毫秒)** **消息类型** **验证模式** **自动提交** 等信息
![编辑kafka消费者触发器](../../../../image/Starlink/Demo/编辑kafka消费者触发器.png)
### elastic job 触发器配置
**说明：**
不支持广播任务，只支持随机任务，即当同一服务部署多台时，任务调度只会调度其中一台执行
#### 新建elasticjob调度触发器
输入触发器名称 选择 触发器类型 ELASTIC_JOB 绑定 函数
![新建elasticjob调度触发器](../../../../image/Starlink/Demo/新建elasticjob调度触发器.png)
#### 编辑elasticjob调度触发器
输入 cron表达式（例如： 0 0/1 * * * ? ） 输入 任务参数（任务参数即绑定的函数的入参 例如 {"param1":"aaa","param2":"bbb"}），任务参数只支持json
![编辑elasticjob调度触发器](../../../../image/Starlink/Demo/编辑elasticjob调度触发器.png)
### http 触发器配置
**说明：**
目前只支持**POST**请求类型 请求数据格式只能是 **json**
#### 新建http API 触发器
输入 **触发器名称** 选择 **触发器类型** HTTP 绑定 **函数** 函数入参就是 请求体数据
![新建http触发器](../../../../image/Starlink/Demo/新建http触发器.png)
#### 查看 http API 触发器
其中链接就是对外暴露的api地址 只支持 https  http会导致函数接收不到请求参数问题
![查看http触发器](../../../../image/Starlink/Demo/查看http触发器.png)


