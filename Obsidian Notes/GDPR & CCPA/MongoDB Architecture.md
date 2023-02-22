## Zones
- With the help of a shard key, MongoDB allows you to create zones of sharded data – also known as shard zones.
- You can associate each zone with one or more shards in the cluster.
- Similarly, A shard can associate with any number of zones.
- MongoDB migrates [chunks](https://www.mongodb.com/docs/v6.0/reference/glossary/#std-term-chunk) covered by a zone only to those shards associated with the zone.
- MongoDB routes reads and writes that fall into a zone range only to those shards inside of the zone.

For GDPR and CCPA we can use this Zone based sharding of MongoDB for segmenting data by geographic area. [Segmenting Data by Location](https://www.mongodb.com/docs/v6.0/tutorial/sharding-segmenting-data-by-location/#segmenting-data-by-location "Permalink to this heading")

> we will shard mongodb first in two regions one is in **NA** and another is in **EU** 

The following diagram illustrates a sharded cluster that uses geographic zones to manage and satisfy GDPR and CCPA compliance.

![[geo_sharded_cluster.png]]

We require one zone per data center. 
**`EU` - European data center**
Shards deployed on this data center are assigned to the `EU` zone.


**`NA` - North American data center**
Shards deployed on this data center are assigned to the `NA` zone.

!!! question "Is defining ranges required in zones?"

    Need to write answer here


### Client-Side Field Level Encryption
