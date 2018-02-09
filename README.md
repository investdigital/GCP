# GCP

## What is this?
    
	This is a GRPC connection pool.

## How to use this?

>  Execute the maven command
       
	maven install
	   
>  Add this dependency to your project

	<dependency>
      <groupId>info.investdigital</groupId>
      <artifactId>GCP</artifactId>
	  <version>1.0-SNAPSHOT</version>
    </dependency>

>  Create a file in your project's resource directory.

    channel.properties
	
>  Add the following configuration

     #------If the value is 20, maintain the number of links when our available connections reach 20 percent of the maximum number of connections
     channel.pool.poolAvailabilityThreshold=20

     #------Minimum number of connections per partition
     channel.pool.minConnectionsPerPartition=20

     #------Maxmum number of connections per partition
     channel.pool.maxConnectionsPerPartition=100

     #------The growth level of the number of connections per partition
     channel.pool.incrConnectNum=20

     #------Gets the timeout of the connection from the connection pool, in seconds
     channel.pool.connectionTimeoutInMs=2

     #------Describes the connection max alive time ,in seconds
     channel.pool.maxConnectionAgeInSeconds=86400

     #------Describes the connection max idle time ,in seconds
     channel.pool.idleMaxAgeInSeconds=3600

     #------Configure the connection pool to maintain the connection port and IP information
     channel.pool.coreConnect=ip:port,ip:port
	 
> How to get a connection?

     ManagedChannelHandle managedChannelHandle =  ManagedChannelPool.getConnection(addr, port);
     ManagedChannel managedChannel = managedChannelHandle.getManagedChannel();

>How to release connection?
     
	 ManagedChannelPool.releaseManagedChannel(managedChannelHandle,addr,port);

## The functionality that has been implemented.
*  Support for connections to multiple services.

## The functions to be implemented in the future.

* Automatic recovery connection
* A friendly connection to a single service.
