# JanusGraph Auth Setup

```shell script
docker-compose up
```

### Test 
```shell script
curl -v -XPOST http://localhost:8182 -d '{"gremlin": "g.V().count()"}' -u user:password

```
