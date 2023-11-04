# Overview

Splunk's HTTP Event Collector (HEC) is a method of ingest into a Splunk deployment. It can run on either a standalone Splunk deployment, a Heavy Forwarder (HF), or on an indexer. The main focus of these load balancer configurations will be on the distributed deployment of Splunk where it will be a load balancer distributing data amongst several targets behind the load balancer.

## Guidelines for optimizing a load balancer to distribute to HEC

The following are what a load balancer should attempt to do in order to best deliver data via HEC to a Splunk deployment:

- evenly distribute data amongst all search peers (indexers)
- minimize connection resets / recreations with the indexers
- minimize connection resets / recreations from the clients to the load balancer
- correctly handle TLS requirements
- handle HEC ACK correctly (if needed and used)
- perform health checks

The above can usually be accomplished in most of the load balancer and revere proxy tools available today.