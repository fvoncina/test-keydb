# KeyDB CLI
```sh
brew install keydb
```

# Redis Stack CLI
```sh
brew tap redis-stack/redis-stack
brew install redis-stack
```

# Region A

## Master
Host: keydb-a-master  
External Port: 6379

   
     
# Region B

## Master
Host: keydb-b-master  
External Port: 16379


# Configurations  

## 497: replicaof   
Crossed between servers   

Master A  
```
replicaof keydb-b-master 6379
```   

Master B   
```
replicaof keydb-a-master 6379
```   

## 2058: Active Replica   
Both servers   

```
active-replica yes
```

# Benchmark


```sh
redis-benchmark -p 6379 -n 1000000 -d 1024 -P 50 -c 100 -t set,get -q
```