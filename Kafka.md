# Kafka



# 读书笔记
## Apache Kafka实战 - 胡夕

- P27 -- Kafka就是依靠下列 4点达到了高吞吐量、低延时的设计目标的

> 大量使用操作系统页缓存，内存操作速度快且命中率高
> 
> Kafka不直接参与物理 1/0操作，而是交由最擅长此事的操作系统来完成
> 
> 采用追加写入方式，摒弃了缓慢的磁盘随机读/写操作
> 
> 使用以 sendfile为代表的零拷贝技术加强网络间的数据传输效率
> 

### topic,partition,offset
- Kafka中的一条消息其实就是一个<topic,partition,offset>三元组(阳ple)，通过该元组值可以在Kafka集群中找到唯一对应的那条消息

### replica（P34）
- replica用于实现日志备份，防止数据丢失
- 副本分为两类:领导者副本(leader replica)和追随者副本(follower replica) 
- follower只是被动地追随leader的状态，保持与leader的同步
- follower存在的唯一价值就是充当leader的候补:一旦leader挂掉立即就会有一个追随者被选举成为新的leader接替它的工作
- Kafka保证同一个partition的多个replica一定不会分配在同一台broker上

### ISR(P35)

- ISR的全称是in-sync replica，就是与leader replica保持同步的replica集合
- Kafka为partition动态维护一个replica集合,该集合中的所有replica保存的消息日志都与leader replica保持同步状态
- 只有这个集合中的replica才能被选举为leader，也只有该集合中所有replica都接收到了同一条消息，Kafka才会将该消息置于“己提交”状态，即认为这条消息发送成功
- 正常情况下，partition的所有replica都应该与leader replica保持同步，即所有 replica都在ISR中
- 因为各种各样的原因，一小部分replica开始落后于leader replica的进度。当滞后到一定程度时，Kafka会将这些replica “踢”出 ISR
- 相反地，当这些replica重新“追上”了leader的进度时，那么Kafka会将它们加回到ISR中

### Zookeeper集群

- P66 - 生产环境中最好的Zookeeper集群节点数量是3台；5台构成的集群比较常见

