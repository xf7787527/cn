# 硬件平台适配

为了适应不同的硬件平台，SDK抽象出了平台相关的接口函数定义，需要开发者根据自身的硬件平台进行适配，头文件路径为 pal/inc，文件列表及说明如下：

| 文件名           | 功能说明           | 备注     |
| :--------------- | :----------------- | :------- |
| joylink_log.h    | 日志打印           | 无需适配 |
| joylink_memory.h | 内存相关接口       | 适配     |
| joylink_mqtt.h   | MQTT客户端相关接口 | 适配     |
| joylink_stdint.h | 整型数定义         | 适配     |
| joylink_stdio.h  | 标准输入输出       | 适配     |
| joylink_string.h | 字符串接口         | 适配     |
| joylink_thread.h | 线程接口           | 适配     |
| joylink_time.h   | 时间相关接口       | 适配     |



# MQTT客户端适配



MQTT客户端需要适配的接口函数定义在pal/inc/ joylink_mqtt.h 头文件中，目前SDK提供了使用mosquitto进行适配的示例，具体参见 pal/src/joylink_mqtt.c 文件```__MQTT_MOSQUITTO_PAL__```宏定义中的代码。

如果您使用的硬件平台有自己的MQTT客户端，根据头文件抽象出的函数接口定义完成适配即可，需要的适配接口函数及说明如下：

| 函数                               | 说明                 |
| :--------------------------------- | :------------------- |
| jl_platform_mqtt_create            | 创建客户端           |
| jl_platform_mqtt_destory           | 销毁客户端           |
| jl_platform_mqtt_connect           | 连接broker           |
| jl_platform_mqtt_disconnect        | 断开与broker的连接   |
| jl_platform_mqtt_yield             | 循环执行函数         |
| jl_platform_mqtt_subscribe         | 消息订阅函数         |
| jl_platform_mqtt_publish           | 消息发布函数         |
| jl_platform_mqtt_set_cb_connect    | 设置连接成功回调函数 |
| jl_platform_mqtt_set_cb_disconnect | 设置连接断开回调函数 |
| jl_platform_mqtt_set_cb_message    | 设置消息回调函数     |