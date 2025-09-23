# kind

Ferramenta que cria um cluster Kubernetes em uma máquina local. Ele precisa do Docker ou o Podman instalado na máquina.

Podemos usar o Kind em diferentes contextos, tipo: Cluester de Produção, Desenvolvimento, Testes, etc.

## Instalação

No endereço kubernetes.io encontramos as instruções de instalação para as versões dos OS`s.

## Linux x86-64

Baixamos o binário com o comando abaixo.

```bash
[ $(uname -m) = x86_64 ] && curl -Lo ./kind https://kind.sigs.k8s.io/dl/v0.30.0/kind-linux-amd64
```

Transformamos o arquivo em executável

```bash
chmod +x ./kind
```

Em seguida, movemos o arquivo para algum diretório de binários, por exemplo.

```bash
sudo mv ./kind /usr/local/bin/kind
```