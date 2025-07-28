nc -lk 9000  # 启动 Socket 输入源
mvn clean package -DskipTests
docker cp /Users/fangjielun/develop/flink-mobile-data-usage/FlinkHelloWorld/target/FlinkTest-1.0-SNAPSHOT.jar jobmanager:/opt/flink/examples

docker exec jobmanager ./bin/flink run -c com.ververica.Main /opt/flink/examples/FlinkTest-1.0-SNAPSHOT.jar
在 nc 终端输入数据，通过
docker logs taskmanager 查看单词计数输出。