"# ClassicDotNetEureka" 

# Fortune-Teller-Service - ASP.NET 4 WebApi Microservice
ASP.NET 4 WebApi sample app illustrating how to use [Spring Cloud Eureka Server](http://projects.spring.io/spring-cloud/docs/1.0.3/spring-cloud.html#spring-cloud-eureka-server) for registering micro services. The Fortune-Teller-Service registers the fortuneService with the Eureka server upon startup.

Note: This application is built using the Autofac IOC container.

# Pre-requisites - Running on CloudFoundry

1. Installed Pivotal CloudFoundry 1.7+ with Greenhouse (i.e. Windows cell)
2. Installed Spring Cloud Services 1.0.9+
3. Web tools installed and on PATH, (e.g. npm, gulp, etc).  
Note: If you're on Windows and you have VS2015 Update 3, you can add these to your path: C:\Program Files (x86)\Microsoft Visual Studio 14.0\Web\External.

# Setup Service Registry on CloudFoundry
You must first create an instance of the Service Registry service in a org/space.

1. cf target -o myorg -s development
2. cf create-service p-service-registry standard myDiscoveryService
3. Wait for service to be ready. (i.e. cf services .. shows ready) 

# What to expect - CloudFoundry
After building and running the app, you should see something like the following in the logs. 

To see the logs as you startup and use the app: `cf logs fortuneservice`

You should see something like this during startup:
```
2016-11-22T09:31:32.48-0700 [STG/0]      OUT Successfully created container
2016-11-22T09:31:32.49-0700 [STG/0]      OUT Downloading app package...
2016-11-22T09:31:35.02-0700 [STG/0]      OUT Staging...
2016-11-22T09:31:35.02-0700 [STG/0]      OUT Downloaded app package (5.2M)
2016-11-22T09:31:38.27-0700 [STG/0]      OUT Exit status 0
2016-11-22T09:31:38.27-0700 [STG/0]      OUT Staging complete
2016-11-22T09:31:38.27-0700 [STG/0]      OUT Uploading droplet, build artifacts cache...
2016-11-22T09:31:38.27-0700 [STG/0]      OUT Uploading build artifacts cache...
2016-11-22T09:31:38.27-0700 [STG/0]      OUT Uploading droplet...
2016-11-22T09:31:38.34-0700 [STG/0]      OUT Uploaded build artifacts cache (88B)
2016-11-22T09:31:43.62-0700 [STG/0]      OUT Uploaded droplet (5.1M)
2016-11-22T09:31:43.63-0700 [STG/0]      OUT Uploading complete
2016-11-22T09:31:43.70-0700 [STG/0]      OUT Destroying container
2016-11-22T09:31:44.10-0700 [CELL/0]     OUT Creating container
2016-11-22T09:31:45.57-0700 [STG/0]      OUT Successfully destroyed container
2016-11-22T09:31:47.32-0700 [CELL/0]     OUT Successfully created container
2016-11-22T09:31:51.59-0700 [APP/0]      OUT Running ..\tmp\lifecycle\WebAppServer.exe
2016-11-22T09:31:51.63-0700 [APP/0]      OUT PORT == 50706
2016-11-22T09:31:51.64-0700 [APP/0]      OUT 2016-11-22 16:31:51Z|INFO|Port:50706
2016-11-22T09:31:51.64-0700 [APP/0]      OUT 2016-11-22 16:31:51Z|INFO|Webroot:C:\containerizer\6897C4658B9FEC74DC\user\app
2016-11-22T09:31:51.72-0700 [APP/0]      OUT 2016-11-22 16:31:51Z|INFO|Starting web server instance...
2016-11-22T09:31:51.83-0700 [APP/0]      OUT Server Started.... press CTRL + C to stop
```
At this point the Fortune Teller Service is up and running and ready for the [Fortune Teller UI]() to ask for fortunes.
