# CouchDB Cluster

[Apache CouchDB](http://couchdb.apache.org/) is open source database software that focuses on ease of use and having an architecture that "completely embraces the Web".
It has a document-oriented NoSQL database architecture and is implemented in the concurrency-oriented language Erlang; it uses JSON to store 
data, JavaScript as its query language using MapReduce, and HTTP for an API.

This repository is an [Apache Brooklyn](http://brooklyn.apache.org) blueprint for deployment and in-life management of CouchDB Cluster. It is based on 
the single node [brooklyn-couchdb-node](https://github.com/brooklyncentral/brooklyn-couchdb-node) blueprint.


The following config keys are available for the the CouchDB Cluster entity:

| Config Key                          | Default         | Description                                                             |
|-------------------------------------|-----------------|-------------------------------------------------------------------------|
| couchdb.username                    | admin           | The admin username                                                      |
| couchdb.password                    | password        | The admin password                                                      |
| couchdb.nodes                       | 3               | The number of nodes the CouchDB cluster should initial start            |

# Using the Entity

Import the [catalog.bom](./catalog.bom) into your Apache Brooklyn catalog and start it in any required location.

The cluster created will replicate it's data across three nodes, each of which can be actively used. The internal addresses 
for these are published as the list sensor `members.urls` and the external as `members.urls.public` of the cluster entity.