## ModificationSyncService

This Service is a simple REST service that can be called by applications to request locks to shared resources. If the resource is not locked already the request will be granted and recorded. Otherwise the application will be notified that a lock exists so that it can react accordingly, e.g. by notifying the user or postpone the processing of the resource. The business framework of SDACK will use a sync service to synchronize requests to persistent entities if configured accordingly.

The service is part of the esoco-lib level of SDACK. It is implemented as a simple Java application that listens for requests on a certain port \(default 7962 = SYNC\). This makes it simple to run it as a Microservice, e.g. in a Docker container. To connect to a sync service from an application esoco-lib also contains the `ModificationSyncEndpoint` that provides a simple `Endpoint` interface to sync services. For the administration of running sync services the command line tool `ModificationSyncServiceTool` can be used.

### ModificationSyncEndpoint

### ModificationSyncServiceTool



