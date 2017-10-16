
There are some advanced client configuration properties to tune some aspects of Hazelcast Client. You can set them as property name and value pairs through declarative configuration, programmatic configuration, or JVM system property. Please see the [Configuring with System Properties section](/500_Understanding_Configuration/300_Configuring_with_System_Properties.md) to learn how to set these properties.

![image](../images/NoteSmall.jpg)***NOTE:*** *When you want to reconfigure a system property, you need to restart the clients for which the property is modified.*


The table below lists the client configuration properties with their descriptions.

Property Name | Default Value | Type | Description
:--------------|:---------------|:------|:------------
`hazelcast.client.event.queue.capacity`|1000000|string|Default value of the capacity of executor that handles incoming event packets.
`hazelcast.client.event.thread.count`|5|string|Thread count for handling incoming event packets.
`hazelcast.client.heartbeat.interval`|10000|string|Frequency of heartbeat messages sent by the clients to members.
`hazelcast.client.heartbeat.timeout`|60000|string|Timeout for the heartbeat messages sent by the client to members. If no messages pass between client and member within the given time via this property in milliseconds, the connection will be closed.
`hazelcast.client.max.concurrent.invocations`|Integer.MAX_VALUE|string|Maximum allowed number of concurrent invocations. You can apply a constraint on the number of concurrent invocations in order to prevent the system from overloading. If the maximum number of concurrent invocations is exceeded and a new invocation comes in, Hazelcast throws `HazelcastOverloadException`.
`hazelcast.client.invocation.timeout.seconds`|120|string|Time to give up the invocation when a member in the member list is not reachable.
`hazelcast.client.responsequeue.idlestrategy`|block|string|Specifies whether the response thread for internal operations at the client side will be blocked or not. If you use `block` (the default value) the thread will be blocked and need to be notified which can cause a reduction in the performance. If you use `backoff` there will be no blocking. By enabling the backoff mode and depending on your use case, you can get a 5-10% performance improvement. However, keep in mind that this will increase CPU utilization. We recommend you to use backoff with care and if you have a tool for measuring your cluster's performance.
`hazelcast.client.shuffle.member.list`|true|string|The client shuffles the given member list to prevent all clients to connect to the same member when this property is `false`. When it is set to `true`, the client tries to connect to the members in the given order.
`hazelcast.client.statistics.enabled`|false|bool|If set to `true`, it enables collecting the client statistics and sending them to the cluster. When it is `true` you can monitor the clients that are connected to your Hazelcast cluster, using Hazelcast Management Center. Please refer to the [Monitoring Clients section](http://docs.hazelcast.org/docs/management-center/latest/manual/html/Monitoring_Clients.html) in the Hazelcast Management Center Reference Manual for more information.
`hazelcast.client.statistics.period.seconds`|3|int|The period in seconds the client statistics are collected and sent to the cluster. Please refer to the [Monitoring Clients section](http://docs.hazelcast.org/docs/management-center/latest/manual/html/Monitoring_Clients.html) in the Hazelcast Management Center Reference Manual for more information. on the client statistics.
`hazelcast.compatibility.3.6.server`|false|bool|When this property is true, if the client cannot know the server version, it will assume that the server has the version 3.6.x.
`hazelcast.invalidation.max.tolerated.miss.count`|10|int|If missed invalidation count is bigger than this value, relevant cached data will be made unreachable.
`hazelcast.invalidation.reconciliation.interval.seconds`|60|int|Period for which the clients are scanned to compare generated invalidation events with the received ones from Near Cache.
