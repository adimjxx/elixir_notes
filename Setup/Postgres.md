```bash
docker run --name postgres \
  -e POSTGRES_USER=elephant \
  -e POSTGRES_PASSWORD=elephant \
  -e POSTGRES_DB=myElixirApp \
  -p 5432:5432 \
  -v pgdata:/var/lib/postgresql/data \
  -d postgres
```

```bash
psql -h localhost -p 5432 -U elephant -d myElixirApp
```