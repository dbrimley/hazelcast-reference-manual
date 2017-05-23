

You have two options for starting Hazelcast Management Center:

1. Deploy the file `mancenter`-*version*`.war` on your Java application server/container.
2. Start Hazelcast Management Center from the command line and then have the Hazelcast cluster members communicate with it. This means that your members should know the URL of the `mancenter` application before they start.

###### Starting with WAR File

Here are the steps.

- Download the latest Hazelcast ZIP from <a href="http://www.hazelcast.org/download/" target="_blank">hazelcast.org</a>. The ZIP contains the `mancenter`-*version*`.war` file under the directory `mancenter`.
- You can directly start `mancenter`-*version*`.war` file from the command line. The following command will start Hazelcast Management Center on port 8080 with context root 'mancenter' (`http://localhost:8080/mancenter`).

```bash
java -jar mancenter-*version*.war 8080 mancenter
```
###### Enabling TLS/SSL when starting with WAR file

When you start Management Center from the command line, it will serve the pages unencrypted by using "http", by default. To enable TLS/SSL, use the following command line parameters when starting the Management Center:

- `-Dhazelcast.mc.tls.enabled=true` (default is false) 
- `-Dhazelcast.mc.tls.keyStore=path to your keyStore`
- `-Dhazelcast.mc.tls.keyStorePassword=password for your keyStore`
- `-Dhazelcast.mc.tls.trustStore=path to your trustStore`
- `-Dhazelcast.mc.tls.trustStorePassword=password for your trustStore`

You can leave trust store and trust store password values empty to use the system JVM's own trust store.

Following is an example on how to start Management Center with  TLS/SSL enabled from the command line:

```bash
java -Dhazelcast.mc.tls.enabled=true -Dhazelcast.mc.tls.keyStore=/some/dir/selfsigned.jks -Dhazelcast.mc.tls.keyStorePassword=yourpassword -jar mancenter-3.8.2.war 
```

You can access Management Center from the following HTTPS URL on port 8443: `https://localhost:8443/mancenter`

To override the HTTPS port, you can give it as the second argument when starting Management Center. For example:

```bash
java -Dhazelcast.mc.tls.enabled=true -Dhazelcast.mc.tls.keyStore=/dir/to/certificate.jks -Dhazelcast.mc.tls.keyStorePassword=yourpassword -jar mancenter-3.8.2.war 80 443 mancenter 
```

This will start Management Center on HTTP port 80 and HTTPS port 443 with context path `/mancenter`. Note that accessing port 80 with an `http://` prefix will redirect the users to an `https://` URL on port 443. It means that the users will use HTTPS regardless of the version of the URL they use.


###### Starting with an Extra Classpath

You can also start the Management Center with an extra classpath entry (for example, when using JAAS authentication) by using the following command:

```bash
java -cp "mancenter-*version*.war:/path/to/an/extra.jar" Launcher 8080 mancenter 
```

On Windows, the command becomes as follows (semicolon instead of colon):

```bash
java -cp "mancenter-*version*.war;/path/to/an/extra.jar" Launcher 8080 mancenter
```

###### Starting with Scripts
 
Optionally, you can use the scripts `startManCenter.bat` or `startManCenter.sh` located in the directory `mancenter` to start the Management Center.

###### Deploying to Application Server

Or, instead of starting at the command line, you can deploy it to your application server (Tomcat, Jetty, etc.).

If you have deployed `mancenter-*version*.war` in your already-SSL-enabled web container, configure `hazelcast.xml` as follows.

```xml
<management-center enabled="true">
    https://localhost:sslPortNumber/mancenter
</management-center>
```

If you are using an untrusted certificate for your container, which you created yourself, you need to add that certificate to your JVM first. Download the certificate from the browser, after this you can add it to JVM as follows.

`keytool -import -noprompt -trustcacerts -alias <AliasName> -file <certificateFile> -keystore $JAVA_HOME/jre/lib/security/cacerts -storepass <Password>`


#### Launching to Management Center

After you perform the above steps, make sure that `http://localhost:8080/mancenter` is up.

Configure your Hazelcast members by adding the URL of your web application to your `hazelcast.xml`. Hazelcast members will send their states to this URL.

```xml
<management-center enabled="true">
    http://localhost:8080/mancenter
</management-center>
```

Now you can start your Hazelcast cluster, browse to `http://localhost:8080/mancenter` and setup your [administrator account](01_Getting_Started.md) explained in the next section.


###### Configuring Update Interval

You can set a frequency (in seconds) for which Management Center will take information from the Hazelcast cluster, using the element `update-interval` as shown below. `update-interval` is optional and its default value is 3 seconds.

```xml
<management-center enabled="true" update-interval="3">
   http://localhost:8080/mancenter
</management-center>
```
