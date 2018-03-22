### [⤴ SDACK Tools](/tools.md)

## ModificationSyncService

The `ModificationSyncService` is a REST service that can be used to synchronize the access to shared resources from multiple applications. Such resources may be a central database or interfaces to external systems, for example. Applications can request a lock to a certain resource and if the resource is not locked already the request will be granted and recorded. Otherwise the application will be notified that a lock exists so that it can react accordingly, e.g. by notifying the user or postpone the processing of the resource. The business framework of SDACK can use a sync service to synchronize requests to persistent entities in a database.

The service is part of the esoco-lib library of SDACK. It is implemented in Java as a server application that listens for HTTP requests on a certain port \(default 7962 = SYNC\). This makes it simple to run it as a Microservice, e.g. in a Docker container. To connect to a sync service from an application esoco-lib also contains the `ModificationSyncEndpoint` that provides a simple `Endpoint` interface to sync services. For the administration of running sync services the command line tool `ModificationSyncServiceTool` can be used.

The sync service can be accessed through several URLs relative to the service address. Requests to these URLs must be in JSON format which is also returned as the response. The main URL is `/api/sync/` under which the actual synchronization API is available to applications. There are also some additional URLs that can be accessed:

* `/info`: displays some basic informations about the service \(this is also the default if the service address is invoked without a URL
* `/ping` and `/healthcheck`: both return true if the service is up and running. Can be used for monitoring purposes
* `/api/status` provides serveral endpoints to query the service status:
  * `/api/status/uptime`: the uptime of the service in milliseconds
  * `/api/status/start_date`: the start date and time of the service in the standard ISO date-time format
  * `/api/status/current_locks`: the currently held locks, mirrored from the sync API
* /api/control allows to modify 

### ModificationSyncEndpoint

### ModificationSyncServiceTool



