# 平台SDK
平台SDK，是星链引擎提供的集函数和连接器相关API、自定义过滤器、Json工具、字符串工具以及日志打印等为一体的开发者工具包，旨在为平台用户开发VMS提供简单易用的常用功能接口。

**Gradle依赖配置**
```Groovy
compile "com.jd.starlink:starlink-engine-sdk:${STARLINK_ENGINE_VERSION}"
```
## 注解
### @EnvValue
用于注入环境变量。需要注意的是目前环境变量的值都是String，声明的类型非String会报错。

**源码**
```Java
/**
 * 支持环境变量的注入
 */
@Target(value = ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface EnvValue {
    /**
     * 环境变量的KEY，默认是空串。如果是空串，注入时会按注解的字段的名称作为KEY
     * @return 环境变量的KEY
     */
    String name() default "";
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.annotation.EnvValue;

public class Demo{
    @EnvValue
    private String appName;
    @EnvValue(name="appName")
    private String appName1;
}
```
### @Inject
用于注入连接器和函数等平台SDK中的类型，也可以注入用户自定义的类型。用户自定义的类型注入是单例的，通过默认构造方法实例化，所以必须要有无参的构造方法。

**源码**
```Java
/**
 * 只生效于平台函数或者Inject注解的字段的类型的类中，其他类中无法注入
 */
@Target(value = ElementType.FIELD)
@Retention(RetentionPolicy.RUNTIME)
public @interface Inject {
    /**
     * 注入的对象的名称，默认是空串。如果是空串，注入时会按注解的字段名作为注入对象的名称
     * @return KEY的名称
     */
    String name() default "";
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.annotation.Inject;
import com.jd.starlink.engine.sdk.connector.RpcConnector;

public class Demo{
    @Inject
    private RpcConnector queryUser;
    @Inject(name="queryUser")
    private RpcConnector queryUserService;
}
```
## 函数
### Function
函数接口，可以通过此接口调用VMS内的函数。结合@Inject注入函数。

**源码**
```Java
/**
 * 函数对象，可以通过注入的方式在函数中调用其他的函数
 */
public interface Function {
    /**
     *
     * @param params 函数入参
     * @return
     */
    Object invoke(Object... params);
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.annotation.Inject;
import com.jd.starlink.engine.sdk.function.Function;

import java.util.HashMap;
import java.util.Map;

public class Demo{
    /**
     * 通过{@link Inject}注解注入函数对象
     */
    @Inject
    private Function func;
    public Map<String,Object> doCall (Map<String,Object> paramsMap) {
        Map<String,Object> resultMap = new HashMap<>();
        func.invoke(paramsMap);
        return resultMap;
    }
}
```
## 连接器
### DBConnector
DB类连接器的接口，主要用于持久层服务调用，可以通过@Inject注解来注入DB类连接器。

**源码**
```Java
/**
 * DB连接器
 */
public interface DBConnector extends Invoker {
    /**
     *
     * @param methodName
     * @param params
     * @param <T>
     * @return
     */
    <T>T invoke(String methodName, Object... params);
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.annotation.Inject;
import com.jd.starlink.engine.sdk.connector.DBConnector;

import java.util.Date;
import java.util.HashMap;
import java.util.Map;

public class Demo{
    /**
     * 通过{@link Inject}注解注入DB连接器对象
     */
    @Inject
    private DBConnector conn;

    public Map<String,Object> doCall (Map<String,Object> paramsMap) {
        paramsMap.put("time", new Date());
        int m = conn.invoke("updateUser", new Object[]{paramsMap});
        Map<String, Object> res = new HashMap<>();
        res.put("count", m);
        return res;
    }
}
```
### RpcConnector
RPC类连接器的接口，主要用于Http等远程接口调用，可以通过@Inject注解来注入RPC类连接器。

**源码**
```Java
/**
 * RPC连接器
 */
public interface RpcConnector extends Invoker{
    /**
     *
     * @param methodName 方法名
     * @param params Connector入参
     * @return
     */
    Object invoke(String methodName,Object... params);

    /**
     *
     * @param methodName 方法名
     * @param returnType 返回值类型
     * @param params 请求参数
     * @return
     */
    Object invoke(String methodName,Class<?> returnType,Object... params);

    /**
     *
     * @param methodName 方法名
     * @param hiddenParams 隐藏参数
     * @param params 参数
     * @return
     */
    Object invoke( String methodName, Map<String,Object> hiddenParams, Object... params);

    /**
     *
     * @param methodName 方法名
     * @param returnType 返回值类型
     * @param hiddenParams 隐藏参数
     * @param params 请求参数
     * @return
     */
    Object invoke(String methodName,Class<?> returnType,Map<String,Object> hiddenParams,Object... params);
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.annotation.Inject;
import com.jd.starlink.engine.sdk.connector.RpcConnector;

import java.util.HashMap;
import java.util.Map;

public class Demo{
    @Inject
    private RpcConnector httpConnector;

    public Map<String,Object> doCall (Map<String,Object> paramsMap) {
        Map<String,Object> methodParamsMap = new HashMap<>();

        Map<String,Object> cookie = new HashMap<>();
        cookie.put("Cookie", paramsMap.get("cookie"));
        // 设置 cookie 参数 cookie 暂不支持多个拼接
        methodParamsMap.put("cookie", cookie);

        Map<String,Object> body = new HashMap<>();
        body.put("groupId", paramsMap.get("groupId"));
        body.put("engineName", paramsMap.get("engineName"));
        body.put("console", paramsMap.get("console"));
        body.put("tailingLines", paramsMap.get("tailingLines"));
        // 设置请求体参数
        methodParamsMap.put("body", body);

        Map<String,Object> header = new HashMap<>();
        header.put("token", paramsMap.get("token"));
        // 设置 请求头 参数
        methodParamsMap.put("header", header);
        // 同理可以设置 path（路径参数）、query（url参数） 等参数  注意 map 的 key 必须以 path、query、 header、cookie、 body （按需加入即可）
        // 调用 接口返回，返回 map 包含 body(响应体)、headers(响应头)
        Map<String, Object> result = (Map<String, Object>)httpConnector.invoke("getEngineLog", new Object[]{methodParamsMap});
        return result;
    }
}
```
## 过滤器
基于JAVA原生的SPI模式，因此使用SPI注册扩展自定义实现即可：  
1.在resources目录下创建META-INF目录，在META-INF目录下创建services目录  
2.创建文件，文件名为接口名，比如com.jd.starlink.engine.sdk.interceptor.AppFunctionInterceptor，文件内容为这个接口的实现类  
### AppInterceptor
开发者自定义的VMS级别的过滤器接口的通用接口，触发器、函数、连接器的过滤器接口都继承自此接口。开发者不可以直接实现此接口，必须得通过实现触发器、函数、连接器的过滤器接口。

**源码**
```Java
/**
 * VMS级别的过滤器定义，用于用户自定义过滤器
 * 开发者自定义过滤器会在引擎级别的过滤器之后执行
 */
public interface AppInterceptor extends Comparable<AppInterceptor>{
    /**
     *
     * @param supplier 方法的提供者
     * @param args 方法入参
     * @param appInterceptorContext 过滤器的上下文
     * @return 返回方法的执行结果
     */
    Object around(Supplier<Object> supplier, Object[] args, AppInterceptorContext appInterceptorContext);
    /**
     * 拦截器的优先级
     * @return 数字越大优先级越高
     */
    default Integer order(){return Integer.MIN_VALUE;}
 
    /**
     * 比较方法，主要用于拦截器的优先级比较
     * @param interceptor 拦截器对象
     * @return a negative integer, zero, or a positive integer as this object is less than, equal to, or greater than the specified object.
     */
    @Override
    default int compareTo( AppInterceptor interceptor){
        return interceptor.order().compareTo(order());
    }
}
```
### AppInterceptorContext
过滤器上下文，保存了当前执行的触发器、函数、连接类型，名称以及执行的方法名等信息。AppInterceptorContext是不可变的对象。

**源码**
```Java
/**
 * 过滤器上下文
 */
@Getter
@AllArgsConstructor
public class AppInterceptorContext {
    /**
     * 触发器、函数、连接器的类型，比如JSF
     */
    private final String type;
    /**
     * 触发器、函数、连接器的名称
     */
    private final String name;
    /**
     * 执行的方法名
     */
    private final String methodName;
}
```
### AppTriggerInterceptor
支持自定义的VMS级别的触发器过滤器接口。继承自AppInterceptor接口。

**源码**
```Java
/**
 * 用户级别的触发器过滤器
 */
public interface AppTriggerInterceptor extends AppInterceptor{
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.interceptor.AppInterceptorContext;
import com.jd.starlink.engine.sdk.interceptor.AppTriggerInterceptor;
import com.jd.starlink.engine.sdk.json.JsonUtil;
import com.jd.starlink.engine.sdk.log.Logger;
import com.jd.starlink.engine.sdk.log.LoggerFactory;

import java.util.function.Supplier;

/**
 * 自定义触发器过滤器
 */
public class DemoTriggerInterceptor implements AppTriggerInterceptor {
    private static final Logger logger = LoggerFactory.getLogger(DemoTriggerInterceptor.class);
    @Override
    public Object around(Supplier<Object> supplier, Object[] args, AppInterceptorContext context) {
        //在触发器执行前打印日志
        logger.info("DemoTriggerInterceptor before around args:{},type:{},methodName:{}", JsonUtil.toJson(args),context.getType(),context.getMethodName());
        //通过supplier.get()方法执行真正的触发器逻辑
        Object result = supplier.get();
        //在触发器执行后打印日志
        logger.info("DemoTriggerInterceptor after around result:{},type:{},methodName:{}", JsonUtil.toJson(result),context.getType(),context.getMethodName());
        return result;
    }
}
```
### AppFunctionInterceptor
支持自定义的VMS级别的函数过滤器接口。继承自AppInterceptor接口。

**源码**
```Java
/**
 * 用户级别的函数过滤器
 */
public interface AppFunctionInterceptor extends AppInterceptor{
}
```
### AppConnectorInterceptor
支持自定义的VMS级别的连接器过滤器接口。继承自AppInterceptor接口。

**源码**
```Java
/**
 * 用户级别的连接器过滤器
 */
public interface AppConnectorInterceptor extends AppInterceptor{
}
```
## 工具类
### JsonUtil
Json工具，目前底层是通过Jackson实现的。建议开发者通过JsonUtil来序列化和反序列化JSON串，只有Jackson不支持的功能才引入其他的JSON工具类。使用时需要在Java/Groovy类中`import com.jd.starlink.engine.sdk.json.JsonUtil`。

**源码**
```Java
/**
 * Json 工具类
 */
@NoArgsConstructor(access = AccessLevel.PRIVATE)
public class JsonUtil {
    private static final Json JSON = JsonBuilder.getJson();

    /**
     * object转json字符串
     * @param obj
     * @return
     */
    public static String toJson(Object obj) {
        return JSON.toJson(obj);
    }

    /**
     * json字符串转指定类型对象
     * @param var
     * @param clazz
     * @param <T>
     * @return
     */
    public static  <T>T fromJson(String var, Class<T> clazz) {
        return JSON.fromJson(var, clazz);
    }

    /**
     * object转指定类型对象
     * @param obj
     * @param clazz
     * @param <T>
     * @return
     */
    public static <T>T fromJson(Object obj, Class<T> clazz) {
        return JSON.fromJson(obj, clazz);
    }

    /**
     * json字符串转集合
     * @param var
     * @param collectionClass
     * @param elementClasses
     * @param <T>
     * @return
     */
    public static <T>T fromJson(String var, Class<?> collectionClass, Class<?>... elementClasses) {
        return JSON.fromJson(var, collectionClass, elementClasses);
    }
}
```
### StringUtil
字符串工具，目前提供了判断是否空串、首字母转大写等方法。使用时需要在Java/Groovy类中`import com.jd.starlink.engine.sdk.util.StringUtil`。

**源码**
```Java
/**
 * 字符串工具类
 */
@NoArgsConstructor(access = AccessLevel.PRIVATE)
public class StringUtil {
    /**
     * Returns {@code true} if the string is empty or contains only
     * {@link Character#isWhitespace(int) white space} codepoints,
     * otherwise {@code false}.
     *
     * @return {@code true} if the string is empty or contains only
     *         {@link Character#isWhitespace(int) white space} codepoints,
     *         otherwise {@code false}
     */
    public static boolean isBlank(String string){
        int strLen;
        if (string != null && (strLen = string.length()) != 0){
            for (int i = 0; i< strLen; i++){
                if (!Character.isWhitespace(string.charAt(i))){
                    return false;
                }
            }
        }
        return true;
    }
    public static boolean isNotBlank(String string){
        return !isBlank(string);
    }

    /**
     * Returns {@code true} if, and only if, length is {@code 0}.
     *
     * @return {@code true} if length is {@code 0}, otherwise
     * {@code false}
     */
    public static boolean isEmpty(String string){
        return string == null || string.isEmpty();
    }
    public static boolean isNotEmpty(String string){
        return !isEmpty(string);
    }

    /**
     * 首字母大写
     * @return 首字母大写
     */
    public static String upperCaseFirst(String str) {
        if (str == null || str.length() == 0) {
            return str;
        }
        char firstChar = str.charAt(0);
        if (Character.isUpperCase(firstChar)) {
            return str;
        }
        return Character.toUpperCase(firstChar) + str.substring(1);
    }
}
```
## 日志
### Logger
日志对象类。

**源码**
```Java
/**
 * 日志类
 */
public interface Logger {
    void debug(String msg);

    void debug(Object object);

    void debug(String format, Object... args);

    void debug(String msg, Throwable t);

    void info(String msg);

    void info(Object object);

    void info(String format, Object... args);

    void info(String msg, Throwable t);

    void warn(String msg);

    void warn(Object object);

    void warn(String format, Object... args);

    void warn(String msg, Throwable t);

    void error(String msg);

    void error(Object object);

    void error(String format, Object... args);

    void error(String msg, Throwable t);
}
```
### LoggerFactory
日志工厂类，通过工厂获取日志对象。

**源码**
```Java
/**
 * 日志工厂
 */
public class LoggerFactory {
    private LoggerFactory(){}
    private static LoggerBuilder loggerBuilder;
    public static void setLoggerBuilder(LoggerBuilder loggerBuilder){
        LoggerFactory.loggerBuilder = loggerBuilder;
    }
    /**
     * 非线程池下可使用此方法生成日志对象，支持子线程，但并不支持线程池
     * @return 日志对象
     */
    public static Logger getLogger(){
        return loggerBuilder.getLogger();
    }

    /**
     * 在线程池中使用日志必须此方法获取日志对象
     * 需要传入VMS名称，不然无法将日志打印到对应的VMS上
     * @param name vmsName
     * @return 日志对象
     */
    public static Logger getLogger(String name){
        return loggerBuilder.getLogger(name);
    }

    /**
     * 非线程池下可使用此方法生成日志对象，支持子线程，但并不支持线程池
     * @param clazz Class对象
     * @return 日志对象
     */
    public static Logger getLogger(Class<?> clazz){
        return loggerBuilder.getLogger(clazz);
    }

    /**
     * 在线程池中使用日志必须此方法获取日志对象
     * 需要传入VMS名称，不然无法将日志打印到对应的VMS上
     * @param name VMS名称
     * @param clazz Class对象
     * @return 日志对象
     */
    public static Logger getLogger(String name, Class<?> clazz){
        return loggerBuilder.getLogger(name, clazz);
    } 
}
```
**示例**
```Java
import com.jd.starlink.engine.sdk.log.Logger;
import com.jd.starlink.engine.sdk.log.LoggerFactory;

import java.util.HashMap;
import java.util.Map;

public class Demo{
    /**
     * 声明LOG，注意使用无参的方法获取Logger对象，通过这种方式的Logger对象不能在线程池中使用
     */
    private final Logger log = LoggerFactory.getLogger();
    /**
     * 如果在线程池中使用，需要使用有参的方法获取Logger对象，入参为VMS名称，而不是当前的类名
     */
    private final Logger log2 = LoggerFactory.getLogger("demo");


    public Map<String,Object> doCall (Map<String,Object> paramsMap) {
        Map<String,Object> resultMap = new HashMap<>();
        log.info("hello world");
        return resultMap;
    }
}
```