# 消费消息（Push）

在使用消息队列 JCQ SDK消费消息的时候可以进行消息过滤。如果多个consumer在同一consumerGroup下，进行消费实现的集群消费的语义；如果多个consumer分别在不同consumerGroup下，进行消费实现的广播消费的语义。

## 可配置参数
| 参数             | 参数描述                                          |
| ---------------- | ------------------------------------------------- |
| filterExpression | 可以设置consumer接收消息的标签（tag），只支持设置一个标签 |

## 示例代码
```Java
package com.jcloud.jcq.sdk.demo;

import com.jcloud.jcq.client.consumer.ConsumeResult;
import com.jcloud.jcq.client.consumer.MessageListener;
import com.jcloud.jcq.common.filter.FilterExpression;
import com.jcloud.jcq.protocol.Message;
import com.jcloud.jcq.sdk.JCQClientFactory;
import com.jcloud.jcq.sdk.auth.UserCredential;
import com.jcloud.jcq.sdk.consumer.Consumer;
import com.jcloud.jcq.sdk.consumer.ConsumerConfig;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

import java.util.List;

/**
 * 推送型消费者 demo.
 * @date 2018-05-17
 */
public class ConsumerDemo {
    private static final Logger logger = LoggerFactory.getLogger(ConsumerDemo.class);
    /**
     * 用户accessKey
     */
    private static final String ACCESS_KEY = "AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA0";
    /**
     * 用户secretKey
     */
    private static final String SECRET_KEY = "BBBBBBBBBBBBBBBBBBBBBBBBBBBBBBB0";
    /**
     * 元数据服务器地址
     */
    private static final String META_SERVER_ADDRESS = "127.0.0.1:18888";
    /**
     * topic名称
     */
    private static final String TOPIC = "testTopic";
    /**
     * 消费组Id
     */
    private static final String CONSUMER_GROUP_ID = "testConsumerGroup";

    public static void main(String[] args) throws Exception {
        // 创建消息consumer, 普通及全局顺序消息都适用
        UserCredential userCredential = new UserCredential(ACCESS_KEY, SECRET_KEY);
        ConsumerConfig consumerConfig = ConsumerConfig.builder()
                .consumerGroupId(CONSUMER_GROUP_ID)
                .metaServerAddress(META_SERVER_ADDRESS)
                .build();
        Consumer consumer = JCQClientFactory.getInstance().createConsumer(userCredential, consumerConfig);

        // 创建消费过滤条件，如果需要
        FilterExpression filterExpression = new FilterExpression();
        filterExpression.setExpressionType(FilterExpression.ExpressionType.TAG);
        filterExpression.setExpression("TAG");

        // 订阅topic，有过滤条件
        consumer.subscribeTopic(TOPIC, new MessageListener() {
                    @Override
                    public ConsumeResult consumeMessages(List<Message> list) {
                        logger.info("messages:{}", list);
                        return ConsumeResult.SUCCESS;
                    }
                },
                filterExpression);

        // 订阅topic1, 无过滤条件
        consumer.subscribeTopic("testTopic1", new MessageListener() {
                    @Override
                    public ConsumeResult consumeMessages(List<Message> list) {
                        logger.info("messages:{}", list);
                        return ConsumeResult.SUCCESS;
                    }
                },
                null);

        // 开启consumer,开始消费
        consumer.start();
    }
}
```

