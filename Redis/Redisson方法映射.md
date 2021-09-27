|      | Redis命令         | Redisson对象方法                                             |
| ---- | ----------------- | ------------------------------------------------------------ |
|      | AUTH              | Config.setPassword();                                        |
|      | APPEND            | RBinaryStream.getOutputStream().write()                      |
|      | BITCOUNT          | RBitSet.cardinality(), RBitSet.cardinalityAsync(), RBitSetReactive.cardinality() |
|      | BITOP             | RBitSet.or(), RBitSet.orAsync(), RBitSetReactive.or(); RBitSet.and(), RBitSet.andAsync(), RBitSetReactive.and(); RBitSet.not(); RBitSet.xor(), RBitSet.xorAsync(), RBitSetReactive.xor() |
|      | BITPOS            | RBitSet.length(), RBitSet.lengthAsync(), RBitSetReactive.length() |
|      | BLPOP             | RBlockingQueue.take(), RBlockingQueue.takeAsync(), RBlockingQueueReactive.take(); RBlockingQueue.poll(), RBlockingQueue.pollAsync(), RBlockingQueueReactive.poll(); RBlockingQueue.pollFromAny(), RBlockingQueue.pollFromAnyAsync(), RBlockingQueueReactive.pollFromAny(); |
|      | BRPOP             | RBlockingDeque.takeLast(), RBlockingDeque.takeLastAsync(), RBlockingDequeReactive.takeLast(); |
|      | BRPOPLPUSH        | RBlockingQueue.pollLastAndOfferFirstTo(), RBlockingQueue.pollLastAndOfferFirstToAsync(), RBlockingQueueReactive.pollLastAndOfferFirstTo(); |
|      | COPY              | RObject.copy, RObject.copyAsync, RObjectReactive.copy();     |
|      | CLIENT SETNAME    | Config.setClientName();                                      |
|      | CLUSTER INFO      | ClusterNode.info();                                          |
|      | CLUSTER KEYSLOT   | RKeys.getSlot(), RKeys.getSlotAsync(), RKeysReactive.getSlot(); |
|      | CLUSTER NODES     | Used in ClusterConnectionManager                             |
|      | DUMP              | RObject.dump(), RObject.dumpAsync(), RObjectReactive.dump(); |
|      | DBSIZE            | RKeys.count(), RKeys.countAsync(), RKeysReactive.count();    |
|      | DECR              | RAtomicLong.decrementAndGet(), RAtomicLong.decrementAndGetAsync(), RAtomicLongReactive.decrementAndGetAsync(); |
| √    | DEL               | RObject.delete(), RObject.deleteAsync(), RObjectReactive.delete(); RKeys.delete(), RKeys.deleteAsync(); |
|      | STRLEN            | RBucket.size(), RBucket.sizeAsync(), RBucketReactive.size(); |
|      | EVAL              | RScript.eval(), RScript.evalAsync(), RScriptReactive.eval(); |
|      | CLIENT REPLY      | RBatch.executeSkipResult();                                  |
|      | EVALSHA           | RScript.evalSha(), RScript.evalShaAsync(), RScriptReactive.evalSha(); |
|      | EXEC              | RBatch.execute(), RBatch.executeAsync(), RBatchReactive.execute(); |
|      | EXISTS            | RObject.isExists(), RObject.isExistsAsync(), RObjectReactive.isExists(); |
|      | FLUSHALL          | RKeys.flushall(), RKeys.flushallAsync(), RKeysReactive.flushall(); |
|      | FLUSHDB           | RKeys.flushdb(), RKeys.flushdbAsync(), RKeysReactive.flushdb(); |
|      | GEOADD            | RGeo.add(), RGeo.addAsync(), RGeoReactive.add();             |
|      | GEODIST           | RGeo.dist(), RGeo.distAsync(), RGeoReactive.dist();          |
|      | GEOHASH           | RGeo.hash(), RGeo.hashAsync(), RGeoReactive.hash();          |
|      | GEOPOS            | RGeo.pos(), RGeo.posAsync(), RGeoReactive.pos();             |
|      | GEORADIUS         | RGeo.radius(), RGeo.radiusAsync(), RGeoReactive.radius(); RGeo.radiusWithDistance(), RGeo.radiusWithDistanceAsync(), RGeoReactive.radiusWithDistance(); RGeo.radiusWithPosition(), RGeo.radiusWithPositionAsync(), RGeoReactive.radiusWithPosition(); |
|      | GEORADIUSBYMEMBER | RGeo.radius(), RGeo.radiusAsync(), RGeoReactive.radius(); RGeo.radiusWithDistance(), RGeo.radiusWithDistanceAsync(), RGeoReactive.radiusWithDistance(); RGeo.radiusWithPosition(), RGeo.radiusWithPositionAsync(), RGeoReactive.radiusWithPosition(); |
|      | GET               | RBucket.get(), RBucket.getAsync(), RBucketReactive.get();    |
|      | GETBIT            | RBitSet.get(), RBitSet.getAsync(), RBitSetReactive.get();    |
|      | GETSET            | RBucket.getAndSet(), RBucket.getAndSetAsync(), RBucketReactive.getAndSet(); RAtomicLong.getAndSet(), RAtomicLong.getAndSetAsync(), RAtomicLongReactive.getAndSet(); RAtomicDouble.getAndSet(), RAtomicDouble.getAndSetAsync(), RAtomicDoubleReactive.getAndSet(); |
|      | HDEL              | RMap.fastRemove(), RMap.fastRemoveAsync(), RMapReactive.fastRemove(); |
|      | HEXISTS           | RMap.containsKey(), RMap.containsKeyAsync(), RMapReactive.containsKey(); |
|      | HGET              | RMap.get(), RMap.getAsync(), RMapReactive.get();             |
|      | HSTRLEN           | RMap.valueSize(), RMap.valueSizeAsync(), RMapReactive.valueSize(); |
|      | HGETALL           | RMap.readAllEntrySet(), RMap.readAllEntrySetAsync(), RMapReactive.readAllEntrySet(); |
|      | HINCRBY           | RMap.addAndGet(), RMap.addAndGetAsync(), RMapReactive.addAndGet(); |
|      | HINCRBYFLOAT      | RMap.addAndGet(), RMap.addAndGetAsync(), RMapReactive.addAndGet(); |
|      | HKEYS             | RMap.readAllKeySet(), RMap.readAllKeySetAsync(), RMapReactive.readAllKeySet(); |
|      | HLEN              | RMap.size(), RMap.sizeAsync(), RMapReactive.size();          |
|      | HMGET             | RMap.getAll(), RMap.getAllAsync(), RMapReactive.getAll();    |
|      | HMSET             | RMap.putAll(), RMap.putAllAsync(), RMapReactive.putAll();    |
|      | HSET              | RMap.put(), RMap.putAsync(), RMapReactive.put();             |
|      | HSETNX            | RMap.fastPutIfAbsent(), RMap.fastPutIfAbsentAsync, RMapReactive.fastPutIfAbsent(); |
|      | HVALS             | RMap.readAllValues(), RMap.readAllValuesAsync(), RMapReactive.readAllValues(); |
|      | INCR              | RAtomicLong.incrementAndGet(), RAtomicLong.incrementAndGetAsync(), RAtomicLongReactive.incrementAndGet(); |
|      | INCRBY            | RAtomicLong.addAndGet(), RAtomicLong.addAndGetAsync(), RAtomicLongReactive.addAndGet(); |
| √    | KEYS              | RKeys.findKeysByPattern(), RKeys.findKeysByPatternAsync(), RKeysReactive.findKeysByPattern(); RedissonClient.findBuckets(); |
|      | LINDEX            | RList.get(), RList.getAsync(), RListReactive.get();          |
|      | LLEN              | RList.size(), RList.sizeAsync(), RListReactive.Size();       |
|      | LPOP              | RQueue.poll(), RQueue.pollAsync(), RQueueReactive.poll();    |
|      | LPUSH             | RDeque.addFirst(), RDeque.addFirstAsync(); RDequeReactive.addFirst(), RDeque.offerFirst(), RDeque.offerFirstAsync(), RDequeReactive.offerFirst(); |
|      | LRANGE            | RList.readAll(), RList.readAllAsync(), RListReactive.readAll(); |
|      | LREM              | RList.fastRemove(), RList.fastRemoveAsync(), RList.remove(), RList.removeAsync(), RListReactive.remove(); RDeque.removeFirstOccurrence(), RDeque.removeFirstOccurrenceAsync(), RDequeReactive.removeFirstOccurrence(); RDeque.removeLastOccurrence(), RDeque.removeLastOccurrenceAsync(), RDequeReactive.removeLastOccurrence(); |
|      | LSET              | RList.fastSet(), RList.fastSetAsync(), RListReactive.fastSet(); |
|      | LTRIM             | RList.trim(), RList.trimAsync(), RListReactive.trim();       |
|      | LINSERT           | RList.addBefore(), RList.addBeforeAsync(), RList.addAfter(), RList.addAfterAsync(), RListReactive.addBefore(), RListReactive.addAfter(); |
|      | MULTI             | RBatch.execute(), RBatch.executeAsync(), RBatchReactive.execute(); |
|      | MGET              | RedissonClient.loadBucketValues();                           |
|      | MIGRATE           | RObject.migrate(), RObject.migrateAsync();                   |
|      | MOVE              | RObject.move(), RObject.moveAsync();                         |
|      | MSET              | RedissonClient.saveBuckets();                                |
|      | PERSIST           | RExpirable.clearExpire(), RExpirable.clearExpireAsync(), RExpirableReactive.clearExpire(); |
|      | PEXPIRE           | RExpirable.expire(), RExpirable.expireAsync(), RExpirableReactive.expire(); |
|      | PEXPIREAT         | RExpirable.expireAt(), RExpirable.expireAtAsync(), RExpirableReactive.expireAt(); |
|      | PFADD             | RHyperLogLog.add(), RHyperLogLog.addAsync(), RHyperLogLogReactive.add(); RHyperLogLog.addAll(), RHyperLogLog.addAllAsync(), RHyperLogLogReactive.addAll(); |
|      | PFCOUNT           | RHyperLogLog.count(), RHyperLogLog.countAsync(), RHyperLogLogReactive.count(); RHyperLogLog.countWith(), RHyperLogLog.countWithAsync(), RHyperLogLogReactive.countWith(); |
|      | PFMERGE           | RHyperLogLog.mergeWith(), RHyperLogLog.mergeWithAsync(), RHyperLogLogReactive.mergeWith(); |
|      | PING              | Node.ping(); NodesGroup.pingAll();                           |
|      | PSUBSCRIBE        | RPatternTopic.addListener();                                 |
|      | PTTL              | RExpirable.remainTimeToLive(), RExpirable.remainTimeToLiveAsync(), RExpirableReactive.remainTimeToLive(); |
|      | PUBLISH           | RTopic.publish                                               |
|      | PUNSUBSCRIBE      | RPatternTopic.removeListener();                              |
| √    | RANDOMKEY         | RKeys.randomKey(), RKeys.randomKeyAsync(), RKeysReactive.randomKey(); |
|      | RESTORE           | RObject.restore(), RObject.restoreAsync, RObjectReactive.restore(); |
|      | RENAME            | RObject.rename(), RObject.renameAsync(), RObjectReactive.rename(); |
|      | RENAMENX          | RObject.renamenx(), RObject.renamenxAsync(), RObjectReactive.renamenx(); |
|      | RPOP              | RDeque.pollLast(), RDeque.pollLastAsync(), RDequeReactive.pollLast(); RDeque.removeLast(), RDeque.removeLastAsync(), RDequeReactive.removeLast(); |
|      | RPOPLPUSH         | RDeque.pollLastAndOfferFirstTo(), RDeque.pollLastAndOfferFirstToAsync(); |
|      | RPUSH             | RList.add(), RList.addAsync(), RListReactive.add();          |
|      | SADD              | RSet.add(), RSet.addAsync(), RSetReactive.add();             |
|      | SCARD             | RSet.size(), RSet.sizeAsync(), RSetReactive.size();          |
|      | SCRIPT EXISTS     | RScript.scriptExists(), RScript.scriptExistsAsync(), RScriptReactive.scriptExists(); |
|      | SCRIPT FLUSH      | RScript.scriptFlush(), RScript.scriptFlushAsync(), RScriptReactive.scriptFlush(); |
|      | SCRIPT KILL       | RScript.scriptKill(), RScript.scriptKillAsync(), RScriptReactive.scriptKill(); |
|      | SCRIPT LOAD       | RScript.scriptLoad(), RScript.scriptLoadAsync(), RScriptReactive.scriptLoad(); |
|      | SDIFFSTORE        | RSet.diff(), RSet.diffAsync(), RSetReactive.diff();          |
|      | SELECT            | Config.setDatabase();                                        |
| √    | SET               | RBucket.set(); RBucket.setAsync(); RBucketReactive.set();    |
|      | SETBIT            | RBitSet.set(); RBitSet.setAsync(); RBitSet.clear(); RBitSet.clearAsync(); |
|      | SETEX             | RBucket.set(); RBucket.setAsync(); RBucketReactive.set();    |
|      | SETNX             | RBucket.trySet(); RBucket.trySetAsync(); RBucketReactive.trySet(); |
|      | SISMEMBER         | RSet.contains(), RSet.containsAsync(), RSetReactive.contains(); |
|      | SINTERSTORE       | RSet.intersection(), RSet.intersectionAsync(), RSetReactive.intersection(); |
|      | SINTER            | RSet.readIntersection(), RSet.readIntersectionAsync(), RSetReactive.readIntersection(); |
|      | SMEMBERS          | RSet.readAll(), RSet.readAllAsync(), RSetReactive.readAll(); |
|      | SMOVE             | RSet.move(), RSet.moveAsync(), RSetReactive.move();          |
|      | SPOP              | RSet.removeRandom(), RSet.removeRandomAsync(), RSetReactive.removeRandom(); |
|      | SREM              | RSet.remove(), RSet.removeAsync(), RSetReactive.remove();    |
|      | SUBSCRIBE         | RTopic.addListener(), RTopicReactive.addListener();          |
|      | SUNION            | RSet.readUnion(), RSet.readUnionAsync(), RSetReactive.readUnion(); |
|      | SUNIONSTORE       | RSet.union(), RSet.unionAsync(), RSetReactive.union();       |
|      | TTL               | RExpirable.remainTimeToLive(), RExpirable.remainTimeToLiveAsync(), RExpirableReactive.remainTimeToLive(); |
| √    | TYPE              | RKeys.getType();                                             |
|      | UNSUBSCRIBE       | RTopic.removeListener(), RTopicReactive.removeListener();    |
|      | WAIT              | RBatch.syncSlaves, RBatchReactive.syncSlaves();              |
|      | ZADD              | RScoredSortedSet.add(), RScoredSortedSet.addAsync(), RScoredSortedSetReactive.add(); |
|      | ZCARD             | RScoredSortedSet.size(), RScoredSortedSet.sizeAsync(), RScoredSortedSetReactive.size(); |
|      | ZCOUNT            | RScoredSortedSet.count(), RScoredSortedSet.countAsync();     |
|      | ZINCRBY           | RScoredSortedSet.addScore(), RScoredSortedSet.addScoreAsync(), RScoredSortedSetReactive.addScore(); |
|      | ZLEXCOUNT         | RLexSortedSet.lexCount(), RLexSortedSet.lexCountAsync(), RLexSortedSetReactive.lexCount(); RLexSortedSet.lexCountHead(), RLexSortedSet.lexCountHeadAsync(), RLexSortedSetReactive.lexCountHead(); RLexSortedSet.lexCountTail(), RLexSortedSet.lexCountTailAsync(), RLexSortedSetReactive.lexCountTail(); |
|      | ZRANGE            | RScoredSortedSet.valueRange(), RScoredSortedSet.valueRangeAsync(), RScoredSortedSetReactive.valueRange(); |
|      | ZREVRANGE         | RScoredSortedSet.valueRangeReversed(), RScoredSortedSet.valueRangeReversedAsync(), RScoredSortedSetReactive.valueRangeReversed(); |
|      | ZUNIONSTORE       | RScoredSortedSet.union(), RScoredSortedSet.unionAsync(), RScoredSortedSetReactive.union(); |
|      | ZINTERSTORE       | RScoredSortedSet.intersection(), RScoredSortedSet.intersectionAsync(), RScoredSortedSetReactive.intersection(); |
|      | ZRANGEBYLEX       | RLexSortedSet.lexRange(), RLexSortedSet.lexRangeAsync(), RLexSortedSetReactive.lexRange(); RLexSortedSet.lexRangeHead(), RLexSortedSet.lexRangeHeadAsync(), RLexSortedSetReactive.lexRangeHead(); RLexSortedSet.lexRangeTail(), RLexSortedSet.lexRangeTailAsync(), RLexSortedSetReactive.lexRangeTail(); |
|      | ZRANGEBYSCORE     | RScoredSortedSet.valueRange(), RScoredSortedSet.valueRangeAsync(), RScoredSortedSetReactive.valueRange(); RScoredSortedSet.entryRange(), RScoredSortedSet.entryRangeAsync(), RScoredSortedSetReactive.entryRange(); |
|      | TIME              | RedissonClient.getNodesGroup().getNode().time(), RedissonClient.getClusterNodesGroup().getNode().time(); |
|      | ZRANK             | RScoredSortedSet.rank(), RScoredSortedSet.rankAsync(), RScoredSortedSetReactive.rank(); |
|      | ZREM              | RScoredSortedSet.remove(), RScoredSortedSet.removeAsync(), RScoredSortedSetReactive.remove(); RScoredSortedSet.removeAll(), RScoredSortedSet.removeAllAsync(), RScoredSortedSetReactive.removeAll(); |
|      | ZREMRANGEBYLEX    | RLexSortedSet.removeRangeByLex(), RLexSortedSet.removeRangeByLexAsync(), RLexSortedSetReactive.removeRangeByLex(); RLexSortedSet.removeRangeHeadByLex(), RLexSortedSet.removeRangeHeadByLexAsync(), RLexSortedSetReactive.removeRangeHeadByLex(); RLexSortedSet.removeRangeTailByLex(), RLexSortedSet.removeRangeTailByLexAsync(), RLexSortedSetReactive.removeRangeTailByLex(); |
|      | ZREMRANGEBYLEX    | RScoredSortedSet.removeRangeByRank(), RScoredSortedSet.removeRangeByRankAsync(), RScoredSortedSetReactive.removeRangeByRank(); |
|      | ZREMRANGEBYSCORE  | RScoredSortedSet.removeRangeByScore(), RScoredSortedSet.removeRangeByScoreAsync(), RScoredSortedSetReactive.removeRangeByScore(); |
|      | ZREVRANGEBYSCORE  | RScoredSortedSet.entryRangeReversed(), RScoredSortedSet.entryRangeReversedAsync(), RScoredSortedSetReactive.entryRangeReversed(), RScoredSortedSet.valueRangeReversed(), RScoredSortedSet.valueRangeReversedAsync(), RScoredSortedSetReactive.valueRangeReversed(); |
|      | ZREVRANK          | RScoredSortedSet.revRank(), RScoredSortedSet.revRankAsync(), RScoredSortedSetReactive.revRank(); |
|      | ZSCORE            | RScoredSortedSet.getScore(), RScoredSortedSet.getScoreAsync(), RScoredSortedSetReactive.getScore(); |
| ×    | SCAN              | 该方法未发出指令<br />RKeys.getKeys(), RKeysReactive.getKeys(); |
|      | SSCAN             | RSet.iterator(), RSetReactive.iterator();                    |
|      | HSCAN             | RMap.keySet().iterator(), RMap.values().iterator(), RMap.entrySet().iterator(), RMapReactive.keyIterator(), RMapReactive.valueIterator(), RMapReactive.entryIterator(); |
|      | ZSCAN             | RScoredSortedSet.iterator(), RScoredSortedSetReactive.iterator(); |