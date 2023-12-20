# Docker

```bash
docker run -d --name cloudia_db -p 5432:5432 -e POSTGRES_DB=cloudia -e POSTGRES_USER=cloudia -e POSTGRES_PASSWORD=cloudia -p 5432:5432 postgres:15
docker run -d --name cloudia_api -p 8080:8080 cloudia-api:latest
docker run -d --name cloudia_front -p 80:3000 cloudia-front:latest
```
