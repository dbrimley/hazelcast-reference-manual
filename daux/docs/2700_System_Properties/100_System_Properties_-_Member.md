

The table below lists the Hazelcast member system properties with their descriptions in alphabetical order.

You can set them as property name and value pairs through declarative configuration, programmatic configuration, or JVM system property. Please see the [Configuring with System Properties section](/500_Understanding_Configuration/300_Configuring_with_System_Properties.md) to learn how to set these properties.


![image](../images/NoteSmall.jpg)***NOTE:*** *When you want to reconfigure a system property, you need to restart the members for which the property is modified.*



Property Name | Default Value | Type | Description
:--------------|:---------------|:------|:------------
`hazelcast.application.validation.token`|n/a|string|This property can be used to verify that Hazelcast members only join when their application level configuration is the same.
`hazelcast.backpressure.backoff.timeout.millis`|60000|int|Controls the maximum timeout in milliseconds to wait for an invocation space to be available. The value needs to be equal to or larger than 0.
`hazelcast.backpressure.enabled`|false|bool|Enable back pressure.
`hazelcast.backpressure.max.concurrent.invocations.per.partition`|100|int|The maximum number of concurrent invocations per partition.
`hazelcast.backpressure.syncwindow`|1000|string|Used when back pressure is enabled. The larger the sync window value, the less frequent a asynchronous backup is converted to a sync backup.
`hazelcast.cache.invalidation.batch.enabled`|true|bool|Specifies whether the cache invalidation event batch sending is enabled or not.
`hazelcast.cache.invalidation.batch.size`|100|int|Defines the maximum number of cache invalidation events to be drained and sent to the event listeners in a batch.
`hazelcast.cache.invalidation.batchfrequency.seconds`|5|int|Defines cache invalidation event batch sending frequency in seconds.
`hazelcast.clientengine.thread.count`|-1|int|Maximum number of threads to process non-partition-aware client requests, like `map.size()`, query, executor tasks, etc. Default count is 20 times number of cores.
`hazelcast.diagnostics.max.rolled.file.count`|10|int|Allowed count of diagnostic files within each roll.
`hazelcast.diagnostics.max.rolled.file.size.mb`|10|int| Size of each diagnostic file to be rolled.
`hazelcast.invalidation.max.tolerated.miss.count`|10|int|If missed invalidation count is bigger than this value, relevant cached data will be made unreachable.
`hazelcast.invalidation.reconciliation.interval.seconds`|60|int|Period for which the cluster members are scanned to compare generated invalidation events with the received ones from Near Cache.
`hazelcast.client.max.no.heartbeat.seconds`|300|int|Time after which the member assumes the client is dead and closes its connections to the client.
`hazelcast.compatibility.3.6.client`|false|bool|When this property is true, if the server cannot determine the connected client version, it will assume that it has the version 3.6.x. This property is especially needed if you are using ICache (or JCache).
`hazelcast.connect.all.wait.seconds` | 120 | int | Timeout to connect all other cluster members when a member is joining to a cluster.
`hazelcast.connection.monitor.interval` | 100 | int  |   Minimum interval in milliseconds to consider a connection error as critical.
`hazelcast.connection.monitor.max.faults` | 3 | int  |   Maximum IO error count before disconnecting from a member.
`hazelcast.discovery.public.ip.enabled` | false | bool | Enable use of public IP address in member discovery with Discovery SPI.
`hazelcast.enterprise.license.key` | null | string  |   <a href="http://www.hazelcast.com/products.jsp" target="_blank">Hazelcast IMDG Enterprise</a> license key.
`hazelcast.event.queue.capacity` | 1000000 | int | Capacity of internal event queue.
`hazelcast.event.queue.timeout.millis` | 250 | int | Timeout to enqueue events to event queue.
`hazelcast.event.thread.count` | 5 | int | Number of event handler threads.
`hazelcast.graceful.shutdown.max.wait` | 600 | int  |   Maximum wait in seconds during graceful shutdown.
`hazelcast.http.healthcheck.enabled`|false|bool|Enable/disable Hazelcast's HTTP based health check implementation.  When it is enabled, you can retrieve information about your cluster's health status (member state, cluster state, cluster size, etc.) by launching `http://<your member's host IP>:5701/hazelcast/health`.
`hazelcast.health.monitoring.delay.seconds`|30|int|Health monitoring logging interval in seconds.
`hazelcast.health.monitoring.level`|SILENT|string|Health monitoring log level. When *SILENT*, logs are printed only when values exceed some predefined threshold. When *NOISY*, logs are always printed periodically. Set *OFF* to turn off completely.
`hazelcast.heartbeat.interval.seconds` | 5 | int  |   Heartbeat send interval in seconds.
`hazelcast.hidensity.check.freememory`|true|bool|If enabled and is able to fetch memory statistics via Java's `OperatingSystemMXBean`, it checks whether there is enough free physical memory for the requested number of bytes. If the free memory checker is disabled (false), acts as if the check is succeeded.
`hazelcast.icmp.enabled` | false | bool  |   Enable ICMP ping.
`hazelcast.icmp.timeout` | 1000 | int |   ICMP timeout in milliseconds.
`hazelcast.icmp.ttl` | 0 | int |   ICMP TTL (maximum numbers of hops to try).
`hazelcast.initial.min.cluster.size` | 0 | int  |   Initial expected cluster size to wait before member to start completely.
`hazelcast.initial.wait.seconds` | 0 | int  |   Initial time in seconds to wait before member to start completely.
`hazelcast.internal.map.expiration.cleanup.operation.count`|3|int|This is a property which is used internally and subject to change in the future releases.
`hazelcast.internal.map.expiration.cleanup.percentage`|10|int|This is a property which is used internally and subject to change in the future releases.
`hazelcast.internal.map.expiration.task.period.seconds`|5|int|This is a property which is used internally and subject to change in the future releases.
`hazelcast.io.balancer.interval.seconds`|20|int|Interval in seconds between IOBalancer executions.
`hazelcast.io.input.thread.count` | 3 | int | Number of socket input threads.
`hazelcast.io.output.thread.count` | 3 | int | Number of socket output threads.
`hazelcast.io.thread.count` | 3 | int | Number of threads performing socket input and socket output. If, for example, the default value (3) is used, it means there are 3 threads performing input and 3 threads performing output (6 threads in total).
`hazelcast.jcache.provider.type`|n/a|string|Type of the JCache provider. Values can be `client` or `server`.
`hazelcast.jmx` | false | bool  |   Enable [JMX](/17_Management/02_Monitoring_with_JMX.md) agent.
`hazelcast.legacy.memberlist.format.enabled`  | false  |  bool  |  Enables the legacy (for the releases before Hazelcast 3.9) member list format which is printed in the logs. The new format is introduced starting with Hazelcast 3.9 and includes member list version. Any change in the cluster, such as a member leaving or joining, will increment the member list version.<br>Please see the [Starting the Member and Client section](/300_Getting_Started/600_Starting_the_Member_and_Client.md).
`hazelcast.local.localAddress`| | string | It is an overrider property for the default server socket listener's IP address. If this property is set, then this is the address where the server socket is bound to.
`hazelcast.local.publicAddress`| | string | It is an overrider property for the default public address to be advertised to other cluster members and clients.
`hazelcast.lock.max.lease.time.seconds`|Long.MAX_VALUE | long | All locks which are acquired without an explicit lease time use this value (in seconds) as the lease time. When you want to set an explicit lease time for your locks, you cannot set it to a longer time than this value.
`hazelcast.logging.type` | jdk | enum |   Name of [logging](/04_Setting_Up_Clusters/09_Logging_Configuration.md) framework type to send logging events.
`hazelcast.mancenter.home` | mancenter | string |  Folder where Management Center data files are stored (license information, time travel information, etc.).
`hazelcast.map.entry.filtering.natural.event.types` | false | bool | Notify [entry listeners with predicates](/06_Distributed_Data_Structures/00_Map/10_Listening_to_Map_entries_with_Predicates.md) on map entry updates with events that match entry, update or exit from predicate value space.
`hazelcast.map.expiry.delay.seconds`|10|int|Useful to deal with some possible edge cases. For example, when using EntryProcessor, without this delay, you may see an EntryProcessor running on owner partition found a key but EntryBackupProcessor did not find it on backup. As a result of this, when backup promotes to owner, you will end up an unprocessed key.
`hazelcast.map.invalidation.batchfrequency.seconds` | 10 | int |  If the collected invalidations do not reach the configured batch size, a background process sends them at this interval.
`hazelcast.map.invalidation.batch.enabled` | true | bool|  Enable or disable batching. When it is set to `false`, all invalidations are sent immediately.
`hazelcast.map.invalidation.batch.size`| 100 | int | Maximum number of invalidations in a batch.
`hazelcast.map.load.chunk.size` | 1000 | int |   Chunk size for [MapLoader](/06_Distributed_Data_Structures/00_Map/05_Loading_and_Storing_Persistent_Data.md)'s map initialization process (MapLoader.loadAllKeys()).
`hazelcast.map.replica.wait.seconds.for.scheduled.tasks`|10|int|Scheduler delay for map tasks those will be executed on backup members.
`hazelcast.map.write.behind.queue.capacity`|50000|string|Maximum write-behind queue capacity per member. It is the total of all write-behind queue sizes in a member including backups. Its maximum value is `Integer.MAX_VALUE`. The value of this property is taken into account only if the `write-coalescing` element of the Map Store configuration is `false`. Please refer to the [Map Store section](/06_Distributed_Data_Structures/00_Map/05_Loading_and_Storing_Persistent_Data.md) for the description of the `write-coalescing` element.
`hazelcast.master.confirmation.interval.seconds` | 30 | int  |   Interval at which members send master confirmation.
`hazelcast.mastership.claim.timeout.seconds`  | 120  | int  | Timeout which defines when master candidate gives up waiting for response to its mastership claim. After timeout happens, non-responding member will be removed from the member list.
`hazelcast.max.join.merge.target.seconds`|20|int|Split-brain merge timeout for a specific target.
`hazelcast.max.join.seconds`|300|int| Join timeout, maximum time to try to join before giving.
`hazelcast.max.no.heartbeat.seconds` | 60 | int  |   Maximum timeout of heartbeat in seconds for a member to assume it is dead. ***CAUTION***: *Setting this value too low may cause members to be evicted from the cluster when they are under heavy load: they will be unable to send heartbeat operations in time, so other members will assume that it is dead.*
`hazelcast.max.no.master.confirmation.seconds` | 150 | int  |   Maximum timeout of master confirmation from other members.
`hazelcast.max.wait.seconds.before.join` | 20 | int  |   Maximum wait time before join operation.
`hazelcast.mc.max.visible.instance.count` | 100 | int  |   Management Center maximum visible instance count.
`hazelcast.mc.max.visible.slow.operations.count`|10|int|Management Center maximum visible slow operations count.
`hazelcast.mc.url.change.enabled` | true | bool  |   Management Center changing server url is enabled.
`hazelcast.member.list.publish.interval.seconds` | 600 | int  |   Interval at which master member publishes a member list.
`hazelcast.memcache.enabled`| false | bool |   Enable [Memcache](/1600_Hazelcast_Clients/500_Memcache_Client.md) client request listener service.
`hazelcast.merge.first.run.delay.seconds` | 300 | int |   Initial run delay of [split brain/merge process](/2600_Network_Partitioning) in seconds.
`hazelcast.merge.next.run.delay.seconds` | 120 | int |   Run interval of [split brain/merge process](/2600_Network_Partitioning) in seconds.
`hazelcast.migration.min.delay.on.member.removed.seconds`|5|int|Minimum delay (in seconds) between detection of a member that has left and start of the rebalancing process.
`hazelcast.operation.backup.timeout.millis`|5000|int|Maximum time a caller to wait for backup responses of an operation. After this timeout, operation response will be returned to the caller even no backup response is received.
`hazelcast.operation.call.timeout.millis`| 60000 | int | Timeout to wait for a response when a remote call is sent, in milliseconds.
`hazelcast.operation.fail.on.indeterminate.state`| false | bool | When enabled, an operation fails with `IndeterminateOperationStateException`, if it does not receive backup acks in time with respect to backup configuration of its data structure, or the member which owns primary replica of the target partition leaves the cluster.
`hazelcast.operation.generic.thread.count` | -1 | int | Number of generic operation handler threads. `-1` means CPU core count / 2.
`hazelcast.operation.responsequeue.idlestrategy`|block|string|Specifies whether the response thread for internal operations at the member side will be blocked or not. If you use `block` (the default value) the thread will be blocked and need to be notified which can cause a reduction in the performance. If you use `backoff` there will be no blocking. By enabling the backoff mode and depending on your use case, you can get a 5-10% performance improvement. However, keep in mind that this will increase CPU utilization. We recommend you to use backoff with care and if you have a tool for measuring your cluster's performance.
`hazelcast.operation.thread.count` | -1 | int | Number of partition based operation handler threads. `-1` means CPU core count.
`hazelcast.partition.backup.sync.interval`|30|int|Interval for syncing backup replicas.
`hazelcast.partition.count` | 271 | int  |   Total partition count.
`hazelcast.partition.max.parallel.replications`|5|int|Maximum number of parallel partition backup replication operations per member. When a partition backup ownership changes or a backup inconsistency is detected, the members start to sync their backup partitions. This parameter limits the maximum running replication operations in parallel.
`hazelcast.partition.migration.fragments.enabled` | true | bool | When enabled, which is the default behavior, partitions are migrated/replicated in small fragments instead of one big chunk. Migrating partitions in fragments reduces pressure on the memory and network, since smaller packets are created in the memory and sent through the network. Note that it can increase the migration time to complete.
`hazelcast.partition.migration.interval` | 0 | int |   Interval to run partition migration tasks in seconds.
`hazelcast.partition.migration.stale.read.disabled` | false | bool | Hazelcast allows read operations to be performed while a partition is being migrated. This can lead to stale reads for some scenarios. You can disable stale read operations by setting this system property's value to "true". Its default value is "false", meaning that stale reads are allowed.
`hazelcast.partition.migration.timeout` | 300 | int  |   Timeout for partition migration tasks in seconds.
`hazelcast.partition.table.send.interval`|15|int|Interval for publishing partition table periodically to all cluster members.
`hazelcast.partitioning.strategy.class`|null|string|Class name implementing `com.hazelcast.core.PartitioningStrategy`, which defines key to partition mapping.
`hazelcast.performance.monitor.max.rolled.file.count`|10|int|The PerformanceMonitor uses a rolling file approach to prevent eating too much disk space. This property sets the maximum number of rolling files to keep on disk.
`hazelcast.performance.monitor.max.rolled.file.size.mb`|10|int|The performance monitor uses a rolling file approach to prevent eating too much disk space. This property sets the maximum size in MB for a single file. Every HazelcastInstance gets its own history of log files.
`hazelcast.performance.monitoring.enabled`|n/a|bool|Enable the performance monitor, a tool which allows you to see internal performance metrics. These metrics are written to a dedicated log file.
`hazelcast.performance.monitor.delay.seconds`|n/a|int| The period between successive entries in the performance monitor's log file.
`hazelcast.prefer.ipv4.stack` | true | bool  |   Prefer IPv4 network interface when picking a local address.
`hazelcast.query.max.local.partition.limit.for.precheck`|3|int|Maximum value of local partitions to trigger local pre-check for TruePredicate query operations on maps.
`hazelcast.query.optimizer.type`|RULES|String|Type of the query optimizer. For optimizations based on static rules, set the value to `RULES`. To disable the optimization, set the value to `NONE`.
`hazelcast.query.predicate.parallel.evaluation`|false|bool|Each Hazelcast member evaluates query predicates using a single thread by default. In most cases, the overhead of inter-thread communications overweight can benefit from parallel execution. When you have a large dataset and/or slow predicate, you may benefit from parallel predicate evaluations. Set to `true` if you are using slow predicates or have > 100,000s entries per member.
`hazelcast.query.result.size.limit`|-1|int|Result size limit for query operations on maps. This value defines the maximum number of returned elements for a single query result. If a query exceeds this number of elements, a QueryResultSizeExceededException is thrown. Its default value is -1, meaning it is disabled.
`hazelcast.rest.enabled` | false | bool |   Enable [REST](/1600_Hazelcast_Clients/05_REST_Client.md) client request listener service.
`hazelcast.shutdownhook.enabled` | true | bool  | Enable Hazelcast shutdownhook thread. When this is enabled, this thread terminates the Hazelcast instance without waiting to shutdown gracefully.
`hazelcast.shutdownhook.policy`|TERMINATE|string| Specifies the behavior when JVM is exiting while the Hazelcast instance is still running. It has two values: TERMINATE and GRACEFUL. The former one terminates the Hazelcast instance immediately. The latter, GRACEFUL, initiates the graceful shutdown which can significantly slow down the JVM exit process, but it tries to retain data safety. Note that you should always shutdown Hazelcast explicitly via using the method `HazelcastInstance#shutdown()`. It's not recommended to rely on the shutdown hook, this is a last-effort measure.
`hazelcast.slow.operation.detector.enabled`|true|bool|Enables/disables the [Slow Operation Detector](/19_Performance/03_Slow_Operation_Detector.md).
`hazelcast.slow.operation.detector.log.purge.interval.seconds`|300|int|Purge interval for slow operation logs.
`hazelcast.slow.operation.detector.log.retention.seconds`|3600|int|Defines the retention time of invocations in slow operation logs. If an invocation is older than this value, it will be purged from the log to prevent unlimited memory usage. When all invocations are purged from a log, the log itself will be deleted.
`hazelcast.slow.operation.detector.stacktrace.logging.enabled`|false|bool|Defines if the stacktraces of slow operations are logged in the log file. Stack traces are always reported to the Management Center, but by default, they are not printed to keep the log size small.
`hazelcast.slow.operation.detector.threshold.millis`|10000|int|Defines a threshold above which a running operation in `OperationService` is considered to be slow. These operations log a warning and are shown in the Management Center with detailed information, e.g., stacktrace.
`hazelcast.socket.bind.any` | true | bool | Bind both server-socket and client-sockets to any local interface.
`hazelcast.socket.client.bind`|true|bool|Bind client socket to an interface when connecting to a remote server socket. When set to `false`, client socket is not bound to any interface.
`hazelcast.socket.client.bind.any` | true | bool |   Bind client-sockets to any local interface. If not set, `hazelcast.socket.bind.any` will be used as default.
`hazelcast.socket.client.receive.buffer.size`|-1|int|Hazelcast creates all connections with receive buffer size set according to the `hazelcast.socket.receive.buffer.size`. When it detects a connection opened by a client, then it adjusts the receive buffer size according to this property. It is in kilobytes and the default value is -1.
`hazelcast.socket.client.send.buffer.size`|-1|int|Hazelcast creates all connections with send buffer size set according to the `hazelcast.socket.send.buffer.size`. When it detects a connection opened by a client, then it adjusts the send buffer size according to this property. It is in kilobytes and the default value is -1.
`hazelcast.socket.connect.timeout.seconds`|0|int|Socket connection timeout in seconds. `Socket.connect()` will be blocked until either connection is established or connection is refused or this timeout passes. Default is 0, means infinite.
`hazelcast.socket.keep.alive` | true | bool  | Socket set keep alive (`SO_KEEPALIVE`).
`hazelcast.socket.linger.seconds`|0|int|Set socket `SO_LINGER` option.
`hazelcast.socket.no.delay` | true | bool  |   Socket set TCP no delay.
`hazelcast.socket.receive.buffer.size` | 32 | int | Socket receive buffer (`SO_RCVBUF`) size in KB. If you have a very fast network, e.g., 10gbit) and/or you have large entries, then you may benefit from increasing sender/receiver buffer sizes. Use this property and the next one below tune the size. For example, a send/receive buffer size of 1024 kB is a safe starting point for a 10gbit network.
`hazelcast.socket.send.buffer.size` | 32 | int  | Socket send buffer (`SO_SNDBUF`) size in KB.
`hazelcast.socket.server.bind.any` | true | bool | Bind server-socket to any local interface. If not set, `hazelcast.socket.bind.any` will be used as default.
`hazelcast.tcp.join.port.try.count`|3|int|The number of incremental ports, starting with the port number defined in the network configuration, that will be used to connect to a host (which is defined without a port in TCP/IP member list while a member is searching for a cluster).
`hazelcast.unsafe.mode` | auto | string  | "auto" (the default value) automatically detects whether the usage of `Unsafe` is suitable for a given platform. "disabled" explicitly disables the `Unsafe` usage in your platform. "enforced" enforces the usage of `Unsafe` even if your platform does not support it. This property can only be set by passing a JVM-wide system property.
`hazelcast.phone.home.enabled` | true | bool  |   Enable or disable the sending of phone home data to Hazelcast's phone home server.
`hazelcast.wait.seconds.before.join` | 5 | int  | Wait time before join operation.
`hazelcast.wan.map.useDeleteWhenProcessingRemoveEvents` | false | bool  |   Configures WAN replication for `IMap` on the PASSIVE cluster to remove entries using delete instead of remove and when using `com.hazelcast.enterprise.wan.replication.WanBatchReplication` as an endpoint implementation. The member which receives the event batch in the PASSIVE cluster dispatches WAN events to the partition owners as map merge and remove operations. When using remove operations, the old entry value is sent from the partition owner to the caller even though the caller does not use the old value. This can also lead to issues if the PASSIVE cluster does not contain the class definition for the entry value as the value will try to get deserialized, causing `ClassNotFoundException`s. You can switch to using map remove instead on the PASSIVE cluster with this property. This will both save bandwidth and avoid the exception.

