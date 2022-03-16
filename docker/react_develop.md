# Reactの開発環境

ローカルで `create-react-app {アプリケーション名}` をしたあとに、

**Dockerfile**

```dockerfile
FROM node:16-alpine

WORKDIR /workspace
COPY ./package*.json /workspace

RUN apk update && \
    npm install && \
    npm install -g npm
```

**docker-compose.yml**

```yml
version: "3"

services:
  app:
    build: .
    command: sleep infinity
    volumes:
      - ..:/workspace:cached
      - volume_node_modules:/workspace/node_modules
    ports: 
        - 3000:3000
    environment:
      - GENERATE_SOURCEMAP=false

volumes:
    volume_node_modules:
```

```bash
docker compose build
docker compose up -d
```
