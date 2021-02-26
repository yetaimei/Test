###   1.创建诊断流程

2020-03-18 14:10:22: 任务开始...

2020-03-18 14:10:22: 成功创建诊断流程

### 2.部署诊断代理

2020-03-18 14:10:22: 开始部署诊断代理...

2020-03-18 14:10:24: 部署诊断代理成功

### 3.获取进程ID

2020-03-18 14:10:24: 获取JAVA进程ID...

2020-03-18 14:10:25: 存在唯一进程，将诊断进程号为1的服务

### 4.JVM 参数诊断

2020-03-18 14:10:25: 开始诊断JVM参数...

2020-03-18 14:10:25: 获取JVM参数

2020-03-18 14:10:25: 诊断JVM参数

2020-03-18 14:10:25: 上传JVM参数诊断结果

2020-03-18 14:10:25: JVM参数诊断完成

### 5.CPU Profiling

2020-03-18 14:10:25: 开始CPU数据采集...

2020-03-18 14:10:35: CPU数据采集中, 预计持续5分钟

2020-03-18 14:15:35: CPU数据采集完成

### 6.分析 CPU Profiling 数据

2020-03-18 14:15:35: 停止CPU Profiling...

2020-03-18 14:15:35: CPU数据诊断完成

### 7.分析 GC 日志

2020-03-18 14:15:35: 开始获取GC日志...

2020-03-18 14:15:36: 获取成功，开始分析GC日志

2020-03-18 14:15:36: 上传GC诊断结果

2020-03-18 14:15:36: GC诊断完成

### 8.验收诊断报告

2020-03-18 14:15:36: 诊断完成，生成诊断报告

2020-03-18 14:15:36: 诊断流程关闭



## 诊断建议

| 1    | 未设置 -XX:+UseCMSInitiatingOccupancyOnly 参数，CMS 回收的阈值只在第一次生效 |      |
| ---- | ------------------------------------------------------------ | ---- |
| 2    | 最大堆大小设置过小，如果服务运行正常，请降低机器配置，或在启动参数中使用 -Xmx 指定最大堆大小 |      |
| 3    | 启动时添加 -XX:+PrintFlagsFinal 参数，可以在 JVM 启动时输出所有参数值，便于检查参数是否被覆盖 |      |
| 4    | 在日志中输出 STW 的暂停时间，可定位其他 STW 操作，启动参数中添加 -XX:+PrintGCApplicationStoppedTime 开启 |      |
| 5    | 如果服务存在明显的锁竞争，请使用 -XX:-UseBiasedLocking 参数取消偏向锁 |      |

## 启动参数

```xml-dtd
VM Arguments: jvm_args: -Dconfig.type=stage -Dapp.key=qcs.risk.view -Dfile.encoding=UTF-8 -Dsun.jnu.encoding=UTF-8 -Djava.io.tmpdir=/tmp -Djava.net.preferIPv6Addresses=false -Djetty.defaultsDescriptor=WEB-INF/web.xml -Xmx1024m -Xms1024m -XX:MetaspaceSize=128m -XX:MaxMetaspaceSize=256m -Xmn256m -XX:ParallelCMSThreads=8 -XX:+CMSParallelRemarkEnabled -XX:+ExplicitGCInvokesConcurrent -XX:+CMSPermGenSweepingEnabled -XX:+CMSClassUnloadingEnabled -XX:+HeapDumpOnOutOfMemoryError -XX:+PrintGCDetails -XX:+PrintHeapAtGC -XX:+PrintTenuringDistribution -XX:+UseConcMarkSweepGC -XX:+PrintGCTimeStamps -XX:+PrintGCDateStamps -XX:CMSFullGCsBeforeCompaction=0 -XX:+UseCMSCompactAtFullCollection -XX:CMSInitiatingOccupancyFraction=80 -Xloggc:/opt/meituan/logs/simple/meituan.qcs.service.riskview.gc.log -XX:ErrorFile=/opt/meituan/logs/simple/meituan.qcs.service.riskview.vmerr.log -XX:HeapDumpPath=/opt/meituan/logs/simple/meituan.qcs.service.riskview.heaperr.log -Djetty.webroot=/opt/meituan/apps/meituan.qcs.service.riskview/root -Dconfig.type=stage -Dapp.appkey=meituan.qcs.service.riskview -Djetty.appkey=meituan.qcs.service.riskview java_command: com.sankuai.mms.boot.Bootstrap java_class_path (initial): WEB-INF/classes:WEB-INF/lib/activation-1.1.jar:WEB-INF/lib/aggs-matrix-stats-client-5.6.3.jar:WEB-INF/lib/annotations-2.0.3.jar:WEB-INF/lib/antlr-runtime-3.5.jar:WEB-INF/lib/apacheds-i18n-2.0.0-M15.jar:WEB-INF/lib/apacheds-kerberos-codec-2.0.0-M15.jar:WEB-INF/lib/api-annotations-1.0.2.jar:WEB-INF/lib/api-asn1-api-1.0.0-M20.jar:WEB-INF/lib/api-util-1.0.0-M20.jar:WEB-INF/lib/asm-3.1.jar:WEB-INF/lib/asm-5.1.jar:WEB-INF/lib/asm-commons-5.1.jar:WEB-INF/lib/asm-tree-5.1.jar:WEB-INF/lib/aspectjweaver-1.8.9.jar:WEB-INF/lib/avatar-tracker-2.2.5.jar:WEB-INF/lib/aviator-4.1.2.jar:WEB-INF/lib/avro-1.7.4.jar:WEB-INF/lib/c3p0-0.9.1.2.jar:WEB-INF/lib/c3p0-0.9.5.2.jar:WEB-INF/lib/cat-client-1.7.4.jar:WEB-INF/lib/commons-beanutils-1.9.2.jar:WEB-INF/lib/commons-cli-1.2.jar:WEB-INF/lib/commons-codec-1.11.jar:WEB-INF/lib/commons-collections-3.2.2.jar:WEB-INF/lib/commons-collections4-4.1.jar:WEB-INF/lib/commons-compress-1.4.1.jar:WEB-INF/lib/commons-configuration-1.6.jar:WEB-INF/lib/commons-crypto-1.0.0.jar:WEB-INF/lib/commons-digester-1.8.jar:WEB-INF/lib/commons-httpclient-3.1.jar:WEB-INF/lib/commons-io-2.4.jar:WEB-INF/lib/commons-lang-2.6.jar:WEB-INF/lib/commons-lang3-3.4.jar:WEB-INF/lib/commons-logging-1.2.jar:WEB-INF/lib/commons-math3-3.1.1.jar:WEB-INF/lib/commons-net-3.1.jar:WEB-INF/lib/commons-pool-1.6.jar:WEB-INF/lib/crane-client-1.2.7.jar:WEB-INF/lib/crane-remote-1.2.7.jar:WEB-INF/lib/csc-flow-api-0.0.4.jar:WEB-INF/lib/curator-client-2.7.1.jar:WEB-INF/lib/curator-framework-2.8.0.jar:WEB-INF/lib/curator-recipes-2.7.1.jar:WEB-INF/lib/curvesapi-1.03.jar:WEB-INF/lib/dpsf-net-2.10.3.1.1.jar:WEB-INF/lib/druid-1.1.18.jar:WEB-INF/lib/eagle-api-client-1.0.7-20180822.131517-8.jar:WEB-INF/lib/eagle-restclient-1.0.10.jar:WEB-INF/lib/ehcache-core-2.5.2.jar:WEB-INF/lib/elasticsearch-5.6.3.jar:WEB-INF/lib/elasticsearch-rest-client-5.6.3.jar:WEB-INF/lib/elasticsearch-rest-client-sniffer-5.6.3.jar:WEB-INF/lib/elasticsearch-rest-high-level-client-5.6.3.jar:WEB-INF/lib Launcher Type: SUN_STANDARD
```

## 运行参数

```xml-dtd
-XX:CICompilerCount=3 -XX:+CMSClassUnloadingEnabled -XX:CMSFullGCsBeforeCompaction=0 -XX:CMSInitiatingOccupancyFraction=80 -XX:+CMSParallelRemarkEnabled -XX:ConcGCThreads=8 -XX:ErrorFile=/opt/meituan/logs/simple/meituan.qcs.service.riskview.vmerr.log -XX:+ExplicitGCInvokesConcurrent -XX:+HeapDumpOnOutOfMemoryError -XX:HeapDumpPath=/opt/meituan/logs/simple/meituan.qcs.service.riskview.heaperr.log -XX:InitialHeapSize=1073741824 -XX:MaxHeapSize=1073741824 -XX:MaxMetaspaceSize=268435456 -XX:MaxNewSize=268435456 -XX:MaxTenuringThreshold=6 -XX:MetaspaceSize=134217728 -XX:MinHeapDeltaBytes=196608 -XX:NewSize=268435456 -XX:OldPLABSize=16 -XX:OldSize=805306368 -XX:+PrintGC -XX:+PrintGCDateStamps -XX:+PrintGCDetails -XX:+PrintGCTimeStamps -XX:+PrintHeapAtGC -XX:+PrintTenuringDistribution -XX:+UseCMSCompactAtFullCollection -XX:+UseCompressedClassPointers -XX:+UseCompressedOops -XX:+UseConcMarkSweepGC -XX:+UseParNewGC
```

![image-20200320155910331](https://tva1.sinaimg.cn/large/00831rSTly1gd0g911xnhj31qa0tg429.jpg)

![image-20200320155849215](https://tva1.sinaimg.cn/large/00831rSTly1gd0g8pcu35j31pu0u041b.jpg)