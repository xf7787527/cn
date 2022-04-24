# SDK API 简介
SDK对外提供的头文件及功能如下：

| 文件名 | 说明 |
| :-----| :----- |
| joylink.h | 返回值等相关定义 |
| joylink_protocol.h | 通讯消息结构体定义及一些相关API的定义 |
| joylink_sdk.h | 对外主流程API定义 |



SDK提供的API函数及功能说明如下：

| 函数名 | 说明 |
| :-----| :----- |
| joylink_sdk_config_create | 创建SDK配置信息 |
| joylink_sdk_config_destory | 销毁SDK配置信息 |
| joylink_sdk_create | 创建SDK |
| joylink_sdk_destory | 销毁SDK |
| joylink_sdk_initialise | SDK初始化 |
| joylink_sdk_connect | 连接京瞳AIoT应用管理平台 |
| joylink_sdk_main_loop | 进入主循环，阻塞 |
| joylink_sdk_get_messageId | 获取消息Id |
| joylink_sdk_set_dev_cb_connect | 设置设备回调函数：连接成功 |
| joylink_sdk_set_dev_cb_disconnect | 设置设备回调函数：连接断开 |
| joylink_sdk_prop_version_check | 属性设置时，检测请求版本 |
| joylink_sdk_set_dev_cb_prop_set | 设置设备回调函数：属性设置 |
| joylink_sdk_dev_prop_set_response | 发送属性设置响应 |
| joylink_sdk_set_dev_cb_prop_get | 设置设备回调函数：属性获取 |
| joylink_sdk_dev_prop_get_response | 发送属性获取响应 |
| joylink_sdk_dev_prop_post | 设备属性上报 |
| joylink_sdk_set_dev_cb_func_call | 设置设备回调函数：方法调用 |
| joylink_sdk_dev_func_call_response | 发送方法调用响应 |
| joylink_sdk_dev_evt_online_status_post | 直连设备上线状态上报 |
| joylink_sdk_dev_evt_post | 设备事件上报 |
| joylink_sdk_dev_reg_request | 设备自动注册请求 |
| joylink_sdk_set_dev_cb_reg_res | 设置设备回调函数：自动注册响应 |
| joylink_sdk_dev_thing_model_post | 直连设备物模型上报 |
| joylink_sdk_set_dev_cb_thmd_post_res | 设置设备回调函数：物模型上报响应 |
|  |  |
| joylink_proto_keyvalue_parse_bool | 解析bool值 |
| joylink_proto_keyvalue_pack_bool | 打包bool值 |
| joylink_proto_keyvalue_parse_int32 | 解析int32 |
| joylink_proto_keyvalue_pack_int32 | 打包int32 |
| joylink_proto_keyvalue_parse_double | 解析double |
| joylink_proto_keyvalue_pack_double | 打包double |
| joylink_proto_keyvalue_parse_string | 解析字符串 |
| joylink_proto_keyvalue_pack_string | 打包字符串 |