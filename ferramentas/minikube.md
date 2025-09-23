# Minikube

Ferramenta que cria um cluster Kubernetes em uma máquina local. Ele precisa do Docker instalado na máquina.

## Instalação

```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube && rm minikube-linux-amd64
```

## Inicializando o Cluster

Para inicializar o nosso Cluster o comando abaixo precisa ser executado.

```bash
minikube start
```
