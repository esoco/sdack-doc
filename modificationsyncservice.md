### [⤴](https://apps.timwhitlock.info/emoji/tables/unicode#emoji-modal)[ SDACK Tools](/tools.md)

## ModificationSyncService

The ModificationSyncService is a REST service that can be used to synchronize the access to shared resources from multiple applications. Such resources may be a central database or interfaces to external systems, for example. Applications can request a lock to a certain resource and if the resource is not locked already the request will be granted and recorded. Otherwise the application will be notified that a lock exists so that it can react accordingly, e.g. by notifying the user or postpone the processing of the resource. The business framework of SDACK can use a sync service to synchronize requests to persistent entities in a database.

The service is part of the esoco-lib library of SDACK. It is implemented in Java as a server application that listens for HTTP requests on a certain port \(default 7962 = SYNC\). This makes it simple to run it as a Microservice, e.g. in a Docker container. To connect to a sync service from an application esoco-lib also contains the `ModificationSyncEndpoint` that provides a simple `Endpoint` interface to sync services. For the administration of running sync services the command line tool `ModificationSyncServiceTool` can be used.

The sync service can be accessed through several URLs relative to the service address. The main URL is `/api/sync/` under which the actual synchronization API is available to applications.

### ModificationSyncEndpoint

### ModificationSyncServiceTool



