# JanusGraph Auth Setup

Example implementations to deploy JanusGraph.

- [No Authentication](01-no-auth)
- [Basic HTTP Authentication](02-basic-auth)
- [Simple Authentication and Security Layer (SASL)](03-sasl-hmac-auth)


### Test No Auth Implementation
```shell script
cd 01-no-auth/
docker-compose up

# test
curl -v -XPOST http://localhost:8182 -d '{"gremlin": "g.V().count()"}'
```

### Basic Auth Implementation
```shell script
cd 02-basic-auth/
docker-compose up

# test 
curl -v -XPOST http://localhost:8182 -d '{"gremlin": "g.V().count()"}' -u user:password
```
Refer [https://docs.janusgraph.org/basics/server/#http-basic-authentication](https://docs.janusgraph.org/basics/server/#http-basic-authentication)

### Simple Authentication and Security Layer (SASL)
```
cd 03-sasl-hmac-auth/
docker-compose up

# test
curl http://localhost:8182/session -XGET -u user:password
curl -v http://localhost:8182/session -XPOST -d '{"gremlin": "g.V().count()"}' -H "Authorization: Token dXNlcjoxNTA5NTQ2NjI0NDUzOkhrclhYaGhRVG9KTnVSRXJ5U2VpdndhalJRcVBtWEpSMzh5WldqRTM4MW89"
```
Refer [https://docs.janusgraph.org/basics/server/#authentication-over-http-and-websocket](https://docs.janusgraph.org/basics/server/#authentication-over-http-and-websocket)
