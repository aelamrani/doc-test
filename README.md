## README

<!-- MARKDOWN-AUTO-DOCS:START (CODE:src=https://gh.gravitee.io/gravitee-io/gravitee-service-discovery-eureka/master/README.adoc) -->
<!-- The below code snippet is automatically added from https://gh.gravitee.io/gravitee-io/gravitee-service-discovery-eureka/master/README.adoc -->
```adoc
= Gravitee Service Discovery Eureka Plugin

== Description

Allow Eureka Service Discovery integration with Gravitee Gateway.

== Build

This plugin require :

* Maven 3
* JDK 8

Once built, a plugin archive file is generated in : target/gravitee-service-discovery-eureka-[Version].zip

== Deploy

Just unzip the plugin archive in your gravitee gateway plugin workspace ( default is : ${node.home}/plugins )

== Configuration

The configuration is loaded from the common GraviteeIO Gateway configuration file (gravitee.yml)
All configurations described by official Eureka discovery client documentation are available on the official github repository: https://github.com/Netflix/eureka/wiki
Gravitee Gateway uses Eureka Discovery client v1 and fetch configured Eureka Servers. It does not register the gateway application into Eureka registry.
Please refer the official Eureka documentation for advanced uses and advanced concepts.

And configure with API management your SERVICE_ID for Eureka service discovery.

For Eureka Client Config :

|===
|Property |Required |Description |Type| Default

.^|service-discovery.eureka.serviceUrl
^.^|x
|fully qualified URLs to communicate with eurekaserver. Each value can be a single URL or a comma separated list of alternative locations.
^.^|string
^.^|null

.^|service-discovery.eureka.serviceUrl.default
^.^|-
|DEfault fully qualified URLs to communicate with eurekaserver.
^.^|string
^.^|null

.^|service-discovery.eureka.client.refresh.interval
^.^|-
|Indicates how often(in seconds) to fetch the registry information from the eureka server
^.^|int
^.^|30

.^|service-discovery.eureka.appinfo.replicate.interval
^.^|-
|Indicates how often(in seconds) to replicate instance changes to be replicated to the eureka server.
^.^|boolean
^.^|30

.^|service-discovery.eureka.appinfo.initial.replicate.time
^.^|-
|Indicates how long initially (in seconds) to replicate instance info to the eureka server
^.^|boolean
^.^|40

.^|service-discovery.eureka.serviceUrlPollIntervalMs
^.^|-
|Indicates how often(in seconds) to poll for changes to eureka server information.Eureka servers could be added or removed and this setting controls how soon the eureka clients should know about it.
^.^|int
^.^|300

.^|service-discovery.eureka.eurekaServer.proxyPort
^.^|-
|Gets the proxy port to eureka server if any.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.proxyHost
^.^|-
|Gets the proxy host to eureka server if any.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.proxyUserName
^.^|-
|Gets the proxy user name if any.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.proxyPassword
^.^|-
|Gets the proxy password if any.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.readTimeout
^.^|-
|Indicates how long to wait (in seconds) before a read from eureka server needs to timeout.
^.^|int
^.^|8

.^|service-discovery.eureka.eurekaServer.connectTimeout
^.^|-
|Indicates how long to wait (in seconds) before a connection to eureka server needs to timeout. Note that the connections in the client are pooled by org.apache.http.client.HttpClient and this setting affects the actual connection creation and also the wait time to get the connection from the pool.
^.^|int
^.^|5

.^|service-discovery.eureka.eurekaServer.backupregistry
^.^|-
|Gets the name of the implementation which implements BackupRegistry to fetch the registry information as a fall back option for only the first time when the eureka client starts.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.maxTotalConnections
^.^|-
|Gets the total number of connections that is allowed from eureka client to all eureka servers.
^.^|int
^.^|200

.^|service-discovery.eureka.eurekaServer.maxConnectionsPerHost
^.^|-
|Gets the total number of connections that is allowed from eureka client to a eureka server host.
^.^|int
^.^|50

.^|service-discovery.eureka.eurekaServer.context
^.^|-
|Gets the URL context to be used to construct the service url to contact eureka server when the list of eureka servers come from the DNS. This information is not required if the contract returns the service urls from eurekaServerServiceUrls.
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.port
^.^|-
|Gets the port to be used to construct the service url to contact eureka server when the list of eureka servers come from the DNS.This information is not required if the contract returns the service urls eurekaServerServiceUrls(String).
^.^|string
^.^|null

.^|service-discovery.eureka.eurekaServer.domainName
^.^|-
|Gets the DNS name to be queried to get the list of eureka servers.This information is not required if the contract returns the service urls by implementing serviceUrls.
^.^|string
^.^|null

.^|service-discovery.eureka.region
^.^|-
|Gets the region (used in AWS datacenters) where this instance resides.
^.^|string
^.^|us-east-1

.^|service-discovery.eureka.eurekaserver.connectionIdleTimeoutInSeconds
^.^|-
|Indicates how much time (in seconds) that the HTTP connections to eureka server can stay idle before it can be closed.
^.^|int
^.^|30

.^|service-discovery.eureka.registryRefreshSingleVipAddress
^.^|-
|Indicates whether the client is only interested in the registry information for a single VIP.
^.^|string
^.^|null

.^|service-discovery.eureka.client.heartbeat.threadPoolSize
^.^|-
|The thread pool size for the heartbeatExecutor to initialise with
^.^|int
^.^|5

.^|service-discovery.eureka.client.heartbeat.exponentialBackOffBound
^.^|-
|Heartbeat executor exponential back off related property. It is a maximum multiplier value for retry delay, in case where a sequence of timeouts occurred.
^.^|int
^.^|10

.^|service-discovery.eureka.client.cacheRefresh.threadPoolSize
^.^|-
|The thread pool size for the cacheRefreshExecutor to initialise with
^.^|int
^.^|5

.^|service-discovery.eureka.client.cacheRefresh.exponentialBackOffBound
^.^|-
|Cache refresh executor exponential back off related property. It is a maximum multiplier value for retry delay, in case where a sequence of timeouts occurred.
^.^|int
^.^|10

.^|service-discovery.eureka.eurekaServer.gzipContent
^.^|-
|Indicates whether the content fetched from eureka server has to be compressed whenever it is supported by the server. The registry information from the eureka server is compressed for optimum network traffic.
^.^|boolean
^.^|true

.^|service-discovery.eureka.shouldUseDns
^.^|-
|Indicates whether the eureka client should use the DNS mechanism to fetch a list of eureka servers to talk to. When the DNS name is updated to have additional servers, that information is used immediately after the eureka client polls for that information as specified in eurekaServiceUrlPollIntervalSeconds.
^.^|boolean
^.^|false

.^|service-discovery.eureka.preferSameZone
^.^|-
|Indicates whether or not this instance should try to use the eureka server in the same zone for latency and/or other reason.
^.^|boolean
^.^|true

.^|service-discovery.eureka.printDeltaFullDiff
^.^|-
|Indicates whether to log differences between the eureka server and the eureka client in terms of registry information.
^.^|boolean
^.^|false

.^|service-discovery.eureka.disableDelta
^.^|-
|Indicates whether the eureka client should disable fetching of delta and should rather resort to getting the full registry information.
^.^|boolean
^.^|false

.^|service-discovery.eureka.fetchRemoteRegionsRegistry
^.^|-
|Comma separated list of regions for which the eureka registry information will be fetched. It is mandatory to define the availability zones for each of these regions as returned by availabilityZones. Failing to do so, will result in failure of discovery client startup.
^.^|boolean
^.^|null

.^|service-discovery.eureka.shouldFilterOnlyUpInstances
^.^|-
|Indicates whether to get the applications after filtering the applications for instances with only InstanceStatus UP states.
^.^|boolean
^.^|true

.^|service-discovery.eureka.shouldFetchRegistry
^.^|-
|Indicates whether this client should fetch eureka registry information from eureka server.
^.^|boolean
^.^|true

.^|service-discovery.eureka.dollarReplacement
^.^|-
|Get a replacement string for Dollar sign <code>$</code> during serializing/deserializing information in eureka server.
^.^|string
^.^|_-

.^|service-discovery.eureka.escapeCharReplacement
^.^|-
|Get a replacement string for underscore sign <code>_</code> during serializing/deserializing information in eureka server.
^.^|string
^.^|__

.^|service-discovery.eureka.allowRedirects
^.^|-
|Indicates whether server can redirect a client request to a backup server/cluster. If set to false, the server will handle the request directly, If set to true, it may send HTTP redirect to the client, with a new server locat
^.^|boolean
^.^|false

.^|service-discovery.eureka.shouldOnDemandUpdateStatusChange
^.^|-
|If set to true, local status updates via ApplicationInfoManager will trigger on-demand (but rate limited) register/updates to remote eureka servers
^.^|boolean
^.^|true

.^|service-discovery.eureka.encoderName
^.^|-
|This is a transient config and once the latest codecs are stable, can be removed (as there will only be one)
^.^|string
^.^|null

.^|service-discovery.eureka.decoderName
^.^|-
|This is a transient config and once the latest codecs are stable, can be removed (as there will only be one)
^.^|string
^.^|null

.^|service-discovery.eureka.clientDataAccept
^.^|-
|urekaAccept name for client data accept
^.^|string
^.^|null

.^|service-discovery.eureka.shouldUnregisterOnShutdown
^.^|-
|Indicates whether the client should explicitly unregister itself from the remote server on client shutdown.
^.^|boolean
^.^|true

.^|service-discovery.eureka.shouldEnforceRegistrationAtInit
^.^|-
|Indicates whether the client should enforce registration during initialization. Defaults to false.
^.^|boolean
^.^|false

|===

For Eureka Transport Config :

|===
|Property |Required |Description |Type| Default

.^|service-discovery.eureka.transport.sessionedClientReconnectIntervalSeconds
^.^|-
|-
^.^|int
^.^|0

.^|service-discovery.eureka.transport.retryableClientQuarantineRefreshPercentage
^.^|-
|-
^.^|double
^.^|0.66

.^|service-discovery.eureka.transport.applicationsResolverDataStalenessThresholdSeconds
^.^|-
|-
^.^|int
^.^|300

.^|service-discovery.eureka.transport.applicationsResolverUseIp
^.^|-
|-
^.^|boolean
^.^|false

.^|service-discovery.eureka.transport.asyncResolverRefreshIntervalMs
^.^|-
|-
^.^|int
^.^|300000

.^|service-discovery.eureka.transport.asyncResolverWarmupTimeoutMs
^.^|-
|-
^.^|int
^.^|5000

.^|service-discovery.eureka.transport.asyncExecutorThreadPoolSize
^.^|-
|-
^.^|int
^.^|5

.^|service-discovery.eureka.transport.writeClusterVip
^.^|-
|-
^.^|string
^.^|null

.^|service-discovery.eureka.transport.readClusterVip
^.^|-
|-
^.^|string
^.^|null

.^|service-discovery.eureka.transport.bootstrapResolverStrategy
^.^|-
|-
^.^|string
^.^|null

.^|service-discovery.eureka.transport.useBootstrapResolverForQuery
^.^|-
|-
^.^|boolean
^.^|true

|===

[source, yaml]
.Eureka Client configuration example:

For a basic use (without region and zone)
----
service-discovery:
  eureka:
    serviceUrl:
      default: https://localhost:8007/eureka
----
```
<!-- MARKDOWN-AUTO-DOCS:END -->

