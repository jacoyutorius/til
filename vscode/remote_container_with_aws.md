# AWS CLI と Amplify CLIをインストールした状態で Remote Containerを起動する

```bash
$ tree .devcontainer
.devcontainer
├── Dockerfile
└── devcontainer.json
```

**Dockerfile**

```
FROM mcr.microsoft.com/vscode/devcontainers/javascript-node:0-12

ENV DEBIAN_FRONTEND=noninteractive
RUN apt-get update && apt-get -y install --no-install-recommends java-common zip \
    && wget https://corretto.aws/downloads/latest/amazon-corretto-8-x64-linux-jdk.deb \
    && dpkg --install amazon-corretto-8-x64-linux-jdk.deb \
    && wget https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip \
    && unzip awscli-exe-linux-x86_64.zip \
    && ./aws/install \
    # Clean up
    && rm -f awscli-exe-linux-x86_64.zip \
    && rm -f amazon-corretto-8-x64-linux-jdk.deb \
    && apt-get autoremove -y \
    && apt-get clean -y \
    && rm -rf /var/lib/apt/lists/*
ENV DEBIAN_FRONTEND=dialog

WORKDIR /workspaces
```

**devcontainer.json**

```
// For format details, see https://aka.ms/devcontainer.json. For config options, see the README at:
// https://github.com/microsoft/vscode-dev-containers/tree/v0.209.6/containers/javascript-node
{
	"name": "Node.js",
	"build": {
		"dockerfile": "Dockerfile",
		// Update 'VARIANT' to pick a Node version: 16, 14, 12.
		// Append -bullseye or -buster to pin to an OS version.
		// Use -bullseye variants on local arm64/Apple Silicon.
		"args": {
			"VARIANT": "16-bullseye"
		}
	},
	// Set *default* container specific settings.json values on container create.
	"settings": {
		"terminal.integrated.shell.linux": "/bin/bash"
	},
	// Add the IDs of extensions you want installed when the container is created.
	"extensions": [
		"dbaeumer.vscode-eslint"
	],
	// Mount ~/.aws directory for AWS Amplify CLI and AWS CLI access
	"mounts": [
		"source=${localEnv:HOME}${localEnv:USERPROFILE}/.aws,target=/root/.aws,type=bind,consistency=cached"
	],
	// Use in-container folder (not mounted host directory) as a workspace to speeeeeeed-up the `npx create-react-app` command. See https://github.com/toricls/aws-amplify-sns-workshop-in-vscode/pull/3.
	"workspaceMount": "source=${localWorkspaceFolder},target=/workspace,type=bind,consistency=cached",
	"workspaceFolder": "/workspaces",

	// Use 'forwardPorts' to make a list of ports inside the container available locally.
	"forwardPorts": [
		3000,
		20002
	],
	// Use 'postCreateCommand' to run commands after the container is created.
	"postCreateCommand": "npm install -g @aws-amplify/cli@4.41.2",
	// Comment out connect as root instead. More info: https://aka.ms/vscode-remote/containers/non-root.
	"remoteUser": "node"
}
```

### 参考

- [aws-amplify-sns-workshop-in-vscode](https://github.com/toricls/aws-amplify-sns-workshop-in-vscode)
- [amazon-location-service-geofence-system](https://github.com/Kenichiro-Wada/amazon-location-service-geofence-system)