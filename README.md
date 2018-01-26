# artemis-openshift-example
Simple producer/consumer example app utilizing manageiq-messaging and activemq-artemis in OpenShift

## Minishift setup

- `minishift start`
- `oc login -u developer -p developer`
- `oc new-project artemis`
- `oc create -f template.yml`
- `oc new-app --template=artemis`

## Container logs

The logs from the producer and consumer container will show the messages they are processing

Sample producer logs:

```plain
I, [2018-01-26T21:04:13.845903 #1]  INFO -- : Published to address(queue/test_queue.none), msg(""), headers({:"destination-type"=>"ANYCAST", :persistent=>true, :message_type=>"message 1"})
I, [2018-01-26T21:04:14.846819 #1]  INFO -- : Published to address(queue/test_queue.none), msg(""), headers({:"destination-type"=>"ANYCAST", :persistent=>true, :message_type=>"message 2"})
I, [2018-01-26T21:04:15.848178 #1]  INFO -- : Published to address(queue/test_queue.none), msg(""), headers({:"destination-type"=>"ANYCAST", :persistent=>true, :message_type=>"message 3"})
```

Sample consumer logs:

```plain
I, [2018-01-26T21:04:13.893517 #1]  INFO -- : Message received: queue(queue/test_queue.none), msg(), headers({"subscription"=>"4739583cc2abe8db3f982934b90181c44b6f81e7", "content-length"=>"0", "message-id"=>"20", "destination"=>"queue/test_queue.none", "expires"=>"0", "redelivered"=>"false", "priority"=>"4", "persistent"=>"true", "timestamp"=>"1517000653851", "content-type"=>"text/plain; charset=UTF-8", "_AMQ_ROUTING_TYPE"=>"1", "message_type"=>"message 1", "destination-type"=>"ANYCAST", "ack"=>"20"})
I, [2018-01-26T21:04:13.893820 #1]  INFO -- : Message processed
I, [2018-01-26T21:04:14.855995 #1]  INFO -- : Message received: queue(queue/test_queue.none), msg(), headers({"subscription"=>"4739583cc2abe8db3f982934b90181c44b6f81e7", "content-length"=>"0", "message-id"=>"23", "destination"=>"queue/test_queue.none", "expires"=>"0", "redelivered"=>"false", "priority"=>"4", "persistent"=>"true", "timestamp"=>"1517000654847", "content-type"=>"text/plain; charset=UTF-8", "_AMQ_ROUTING_TYPE"=>"1", "message_type"=>"message 2", "destination-type"=>"ANYCAST", "ack"=>"23"})
I, [2018-01-26T21:04:14.856215 #1]  INFO -- : Message processed
I, [2018-01-26T21:04:15.858861 #1]  INFO -- : Message received: queue(queue/test_queue.none), msg(), headers({"subscription"=>"4739583cc2abe8db3f982934b90181c44b6f81e7", "content-length"=>"0", "message-id"=>"26", "destination"=>"queue/test_queue.none", "expires"=>"0", "redelivered"=>"false", "priority"=>"4", "persistent"=>"true", "timestamp"=>"1517000655848", "content-type"=>"text/plain; charset=UTF-8", "_AMQ_ROUTING_TYPE"=>"1", "message_type"=>"message 3", "destination-type"=>"ANYCAST", "ack"=>"26"})
I, [2018-01-26T21:04:15.859107 #1]  INFO -- : Message processed
```
