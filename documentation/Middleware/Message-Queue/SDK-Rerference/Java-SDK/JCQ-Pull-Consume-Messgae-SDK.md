# 消费消息（Pull）

在使用消息队列 JCQ SDK消费消息的时候可以进行消息过滤。如果多个consumer在同一consumerGroup下，进行消费实现的集群消费的语义；如果多个consumer分别在不同consumerGroup下，进行消费实现的广播消费的语义。

注意: 如果以重启进程方式拉取消息(例如使用linux的计划任务定时拉取)，每次拉取一条消息，则都会拉同一个partition，若此partition无消息则会一直拉不到，建议将拉取逻辑放到循环里，在进程内循环拉取。

## 可配置参数
| 参数             | 参数描述                                          |
| ---------------- | ------------------------------------------------- |
| filterExpression | 可以设置consumer接收消息的标签（tag），只支持设置一个标签 |

## 手动ack的action
| ackAction             | 参数描述                                          |
| ---------------- | ------------------------------------------------- |
| SUCCESS | 消费成功 |
| CONSUME_FAILED | 消费失败 |
| RESEND |要求服务端立即重发 |
| DISCARD | 消息丢弃, 不进行重发。消费失败，但是不用再重发 |

## 示例代码
```Java
package com.jcloud.jcq.sdk.demo;

import com.jcloud.jcq.common.filter.FilterExpression;
import com.jcloud.jcq.common.message.AckAction;
import com.jcloud.jcq.sdk.JCQClientFactory;
import com.jcloud.jcq.sdk.auth.UserCredential;
import com.jcloud.jcq.sdk.consumer.PullConsumer;
import com.jcloud.jcq.sdk.consumer.PullConsumerConfig;
import com.jcloud.jcq.sdk.consumer.async.AsyncAckCallback;
import com.jcloud.jcq.sdk.consumer.async.AsyncPullCallback;
import com.jcloud.jcq.sdk.consumer.model.AckResult;
import com.jcloud.jcq.sdk.consumer.model.PullResult;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;

/**
 * 拉取型消费者 demo.
 *
 * @date 2018-05-17
 */
public class PullConsumerDemo {
    private static final Logger logger = LoggerFactory.getLogger(PullConsumerDemo.class);
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
        // 创建拉取型消费者, 普通及全局顺序消息都适用
        UserCredential userCredential = new UserCredential(ACCESS_KEY, SECRET_KEY);
        PullConsumerConfig pullConsumerConfig = PullConsumerConfig.builder()
                .consumerGroupId(CONSUMER_GROUP_ID)
                .metaServerAddress(META_SERVER_ADDRESS)
                .build();
        PullConsumer pullConsumer = JCQClientFactory.getInstance().createPullConsumer(userCredential, pullConsumerConfig);
        pullConsumer.start();

        // 创建消费过滤条件，如果需要
        FilterExpression filterExpression = new FilterExpression();
        filterExpression.setExpressionType(FilterExpression.ExpressionType.TAG);
        filterExpression.setExpression("TAG1");

        // 同步拉取消息, 当需要指定tag作为过滤条件时，第二个参数填充具体的filterExpression
        PullResult pullResult = pullConsumer.pullMessage(TOPIC, null);
        logger.info("Sync pullResult.resultCode:{}, pullResult.ackIndex:{}, pullResult.messages:{}",
                pullResult.getResultCode(), pullResult.getAckIndex(), pullResult.getMessages());

        // 异步拉取消息,当需要指定tag作为过滤条件时，第二个参数填充具体的filterExpression
        pullConsumer.pullMessageAsync(TOPIC, null, new AsyncPullCallback() {
            @Override
            public void onResult(PullResult pullResult) {
                logger.info("Async pullResult.resultCode:{}, pullResult.ackIndex:{}, pullResult.messages:{}",
                        pullResult.getResultCode(), pullResult.getAckIndex(), pullResult.getMessages());
            }

            @Override
            public void onException(Throwable throwable) {
            }
        });

        // 同步ack消息
        AckResult ackResult = pullConsumer.ackMessage(TOPIC, pullResult.getAckIndex(), AckAction.SUCCESS);
        logger.info("Sync ackResult:{}", ackResult.getResultCode());

        // 异步ack消息
        pullConsumer.ackMessageAsync(TOPIC, pullResult.getAckIndex(), AckAction.SUCCESS, new AsyncAckCallback() {
            @Override
            public void onResult(AckResult ackResult) {
                logger.info("Async ackResult:{}", ackResult.getResultCode());
            }

            @Override
            public void onException(Throwable throwable) {
            }
        });
    }
}
```
