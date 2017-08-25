

You can define various member attributes on your Hazelcast members. You can use these member attributes to tag your members as your business logic requirements.

To define member attribute on a member, you can either:

- provide `MemberAttributeConfig` to your `Config` object,

- or provide member attributes at runtime via attribute setter methods on the `Member` interface.

For example, you can tag your members with their CPU characteristics and you can route CPU intensive tasks to those CPU-rich members.

```java
MemberAttributeConfig fourCore = new MemberAttributeConfig();
memberAttributeConfig.setIntAttribute( "CPU_CORE_COUNT", 4 );
MemberAttributeConfig twelveCore = new MemberAttributeConfig();
memberAttributeConfig.setIntAttribute( "CPU_CORE_COUNT", 12 );
MemberAttributeConfig twentyFourCore = new MemberAttributeConfig();
memberAttributeConfig.setIntAttribute( "CPU_CORE_COUNT", 24 );

Config member1Config = new Config();
config.setMemberAttributeConfig( fourCore );
Config member2Config = new Config();
config.setMemberAttributeConfig( twelveCore );
Config member3Config = new Config();
config.setMemberAttributeConfig( twentyFourCore );

HazelcastInstance member1 = Hazelcast.newHazelcastInstance( member1Config );
HazelcastInstance member2 = Hazelcast.newHazelcastInstance( member2Config );
HazelcastInstance member3 = Hazelcast.newHazelcastInstance( member3Config );

IExecutorService executorService = member1.getExecutorService( "processor" );

executorService.execute( new CPUIntensiveTask(), new MemberSelector() {
  @Override
  public boolean select(Member member) {
    int coreCount = (int) member.getIntAttribute( "CPU_CORE_COUNT" );
    // Task will be executed at either member2 or member3
    if ( coreCount > 8 ) { 
      return true;
    }
    return false;
  }
} );

HazelcastInstance member4 = Hazelcast.newHazelcastInstance();
// We can also set member attributes at runtime.
member4.setIntAttribute( "CPU_CORE_COUNT", 2 );
```

For another example, you can tag some members with a filter so that a member in the cluster can load classes from those tagged members. Please see the [User Code Deployment section](/04_Setting_Up_Clusters/07_User_Code_Deployment_-_BETA.md) for more information.

You can also configure your member attributes through declarative configuration and start your member afterwards. Here is how you can use the declarative approach:

```xml
<member-attributes>
  <attribute name="CPU_CORE_COUNT">4</attribute-name>
</member-attributes>
```