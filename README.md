# Kubernetes Tryouts

Welcome to the Kubernetes Tryouts Git repository! This repository is designed to help you get started with Kubernetes by providing hands-on examples and exercises. Whether you are a beginner looking to explore Kubernetes for the first time or an experienced user seeking to reinforce your skills, this repository has something for everyone.

## Table of Contents

- [Introduction](#introduction)
- [Prerequisites](#prerequisites)
- [Getting Started](#getting-started)
- [Examples](#examples)
- [Contributing](#contributing)
- [License](#license)

## Introduction

Kubernetes is an open-source container orchestration platform that automates the deployment, scaling, and management of containerized applications. This repository aims to make learning Kubernetes an interactive and enjoyable experience.

## Prerequisites

Before you begin, ensure you have the following prerequisites installed on your local machine:

- [Docker](https://www.docker.com/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [minikube](https://minikube.sigs.k8s.io/docs/start/)
- [microk8s](https://microk8s.io/docs/getting-started)

## Getting Started

1. Clone this repository to your local machine:

   ```bash
   git clone https://github.com/prince11jose/kubernetes-tryouts.git
   ```
2. Navigate to the project directory:

```bash

cd kubernetes-tryouts
```
### Install microk8s 
```
sudo snap install microk8s --classic --channel=1.28
sudo usermod -a -G microk8s $USER
sudo chown -f -R $USER ~/.kube
microk8s status --wait-ready
```
### Enable Addons
```
microk8s enable dns
microk8s enable helm
microk8s enable helm3
microk8s enable community
microk8s enable metrics-server
```

## Follow the examples in the Examples section to start experimenting with Kubernetes.

## Examples
Explore various examples in the kubernetes-tryouts directory to understand different aspects of Kubernetes, including:

Pods: Basic deployment and management of pods.
Services: Exposing applications within a cluster.
Deployments: Managing and scaling applications using deployments.
ConfigMaps and Secrets: Managing configuration data and secrets.
Volumes: Persistent storage in Kubernetes.
Feel free to modify and experiment with these examples. Each example includes a README.md file with detailed instructions.

## Contributing
If you find issues or have improvements to suggest, please open an issue or create a pull request. Your contributions are highly welcome!

## Fork the repository.
Create a branch for your feature or bug fix: git checkout -b feature-name.
Make your changes and commit them: git commit -m "Description of changes".
Push your changes to your fork: git push origin feature-name.
Open a pull request.
## License
This project is licensed under the MIT License - see the LICENSE file for details.

Happy Kubernetes exploring!





