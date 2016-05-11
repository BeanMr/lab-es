# ES启动过程分析
ES与很多基于Java开发的程序一样，启动过程是通过shell脚本引导启动JVM进程。
此脚本源码为`distribution/src/main/resources/bin/elasticsearch`，
它主要负责参数的解析、校验、封装，最终调用`java`运行`ElasticSearch`类的`main`函数。
在Shell运行过程中收集的参数会传入`ElasticSearch`类的`main`方法，
`ElasticSearch`类继承自`com.elasticsearch.cli`包的`Command`类。
`Command`类基于`JOpt Simple`完成参数的解析工作并实现了ES的`CLI`模式的交互UI。