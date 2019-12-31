# 读书笔记
## ActiveMQ in Action
+ page 5 : ActiveMQ offers its own style of ultra-fast message persistence via KahaDB, but also supports standard JDBC-accessible databases

+ page 51 : There are three types of properties: custom properties, JMS defined properties, and provider-specific properties.

+ transport connectors : provides client-to-broker communications
+ network connectors : broker-to-broker communications

+ page 332 : advisory messages, which allow you to receive important notifications from the broker in a more messaging-like manner

+ page 367 : Advisory messages are delivered to topics whose names use the prefix ActiveMQ.Advisory
+ For example, if you’re interested in knowing when connections to the bro- ker are started and stopped, you can see this activity by subscribing to the ActiveMQ.Advisory.Connection topic

+ **p188**
+ **p384**

# 网上资源
+ [ActiveMQ失效转移（Failover）](https://manzhizhen.iteye.com/blog/2105572)
