# Docker Compose

Revies the `docker-compose.yml` file.

```yaml
---
version: "3.8"
name: cloudia

networks:
  cloudia:
    driver: bridge

services:
  front:
    image: cloudia/front:latest
    build:
      context: .
      args:
        VITE_APP_BASE_URL: "http://localhost:3000"
        VITE_APP_API_URL: "http://localhost:8080/api"
    ports:
      - "3000:3000"
    networks:
      - cloudia

  api:
    image: cloudia/api:latest
    environment:
        BACKEND_CORS_ORIGINS: '["http://localhost", "http://localhost:4200", "http://localhost:3000", "http://localhost:8080", "http://localhost:8888", "https://localhost", "https://localhost:4200", "https://localhost:3000", "https://localhost:8080"]'
        SECRET_KEY: "4b8c2928092c6701dd6e9379cb9c1ec3ba4064370682154d41fb760f46d3b32a"
        USER_ADMIN_FULLNAME: "Admin"
        USER_ADMIN_EMAIL: "admin@cloudia.fr"
        USER_ADMIN_PASSWORD: "admin"
        USER_TEST_FULLNAME: "Test"
        USER_TEST_EMAIL: "test@cloudia.fr"
        USER_TEST_PASSWORD: "test"
        POSTGRES_SERVER: "db"
        POSTGRES_PORT: "5432"
        POSTGRES_DB: "cloudia"
        POSTGRES_USER: "cloudia"
        POSTGRES_PASSWORD: "cloudia"
        API_KEY_SECRET: "test123"
        # Google Cloud Platform
        GCP_SERVICE_ACCOUNT_JSON_KEY_FILE: "service-account-key-file.json"
        GCP_ORGANIZATION_ID: "512088778395"
        # Amazon Web Services
        AWS_ACCESS_KEY_ID: "AKIAVIHF4467I35RYVV5"
        AWS_SECRET_ACCESS_KEY: "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"
        AWS_DEFAULT_REGION: "us-east-1"
    ports:
        - "8080:8080"
    networks:
      - cloudia

  db:
    image: postgres:15
    environment:
      POSTGRES_DB: cep
      POSTGRES_USER: cep
      POSTGRES_PASSWORD: cep
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U cep"]
      interval: 5s
      timeout: 2s
      retries: 10
    networks:
      - cloudia
```

Run the platform through Docker Compose:

```bash
docker compose up -d
```
