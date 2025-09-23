# kubectl

A ferramenta CLI de controle de clusters Kubernetes. Nele, executamos comandos para gerenciar o nosso cluster.

## Instalação

No endereço kubernetes.io encontramos as instruções de instalação para as versões dos OS`s.

## Linux x86-64

Para baixar o binário do kubectl executamos o comando curl abaixo.

```bash
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
```

Será baixado o arquivo na pasta local e devemos mudar para um executável como o comando a seguir.

```bash
sudo chmod +x kubectl
```

Em seguida, movemos o arquivo para algum diretório de binários, por exemplo.

```bash
sudo mv kubectl /usr/local/bin
```

## Versão do kubectl

Podemos verificar a versão do binário que temos na nossa máquina.

```bash
kubectl version --client
```

## Kubectx

Ferramenta que permite mudar de contexto entre Cluster.

```bash
kubectx default

kubectx minikube
```
