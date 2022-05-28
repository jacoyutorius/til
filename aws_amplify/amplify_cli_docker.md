# VSCode Remote Containersで amplify cliを予めインストールした環境を作る

### 2022/05/28更新

VSCodeRemoteContainerがデフォルトで使っているコンテナイメージを使うのを避けたかったので。
あと、amplify-cliのバージョンも指定するように。

これと、[Reactの開発環境](https://github.com/jacoyutorius/til/blob/main/docker/react_develop.md) に記載している docker-compose.yml
を定義して、VSCode RemoteContainersで docker-compose.ymlのほうを指定して起動するようにする。

**Dockerfile**

```
FROM node:16-alpine

WORKDIR /workspace
COPY ./package*.json /workspace

RUN apk update && \
    npm install && \
    npm install --location=global npm

RUN npm install --location=global @aws-amplify/cli@7.6.26
```


---

(旧)

Dockerifleに以下を追加する。
(以下はDocker imageが `mcr.microsoft.com/vscode/devcontainers/javascript-node:0-16-bullseye` の場合)

```Docker
RUN su node -c "npm install -g @aws-amplify/cli"
```

全体。

```Docker
# See here for image contents: https://github.com/microsoft/vscode-dev-containers/tree/v0.217.4/containers/javascript-node/.devcontainer/base.Dockerfile

# [Choice] Node.js version (use -bullseye variants on local arm64/Apple Silicon): 16, 14, 12, 16-bullseye, 14-bullseye, 12-bullseye, 16-buster, 14-buster, 12-buster
ARG VARIANT="16-bullseye"
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-${VARIANT}

# [Optional] Uncomment this section to install additional OS packages.
# RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
#     && apt-get -y install --no-install-recommends <your-package-list-here>

# [Optional] Uncomment if you want to install an additional version of node using nvm
# ARG EXTRA_NODE_VERSION=10
# RUN su node -c "source /usr/local/share/nvm/nvm.sh && nvm install ${EXTRA_NODE_VERSION}"

# [Optional] Uncomment if you want to install more global node modules
RUN su node -c "npm install -g @aws-amplify/cli"
```