## GraphQL over Leipzig Open Data Catalog

```bash
# Download the catalog in Turtle
wget https://opendata.leipzig.de/catalog.ttl

# Generate a GraphQL Schema
docker run -v "$(pwd):/data" -u "$(id -u):$(id -g)" -i aksw/rpt:graphql-lswt-2025 graphqltk schemagen /data/catalog.ttl > catalog.graphql

# Launch the server
docker run -v "$(pwd):/data" -u "$(id -u):$(id -g)" --network host -i aksw/rpt:graphql-lswt-2025 integrate --server --graphql-schema /data/catalog.graphql /data/catalog.ttl --port 7000
```

