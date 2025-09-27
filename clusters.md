# Cluster

É um conjunto de nodes(nós) que o Kubernetes realiza o gerenciamento.

## Criando um cluster na máquina local

Para criar um cluster padrão sem parâmetros usamos o comando abaixo.

```bash
kind create cluster
```

## Criação do cluster pelo arquivo .yaml

Após a configuração do arquivos .yaml podemos executar o comando abaixo para criar o cluster.

```bash
kind create cluster --config file.yaml --name tux.
```

O parâmetro --config é para informar o nome do arquivo .yaml

O parâmetro --name é para rotular o cluster

## Deletando um cluster na máquina local

Para deletar um cluster padrão sem parâmetros usamos o comando abaixo.

```bash
kind delete cluster
```

Para remover usando o nome do cluster, precisamos do comando abaixo.

```bash
kind delete cluster --name cluster-name
```

## Criando o cluster multinode

Para criar um cluster que tenha vários nós(nodes) precisamos criar uma arquivo .yaml e inserir as informações necessárias para a criação do cluster. Abaixo um exemplo de uma arquivo de configuração.

### Modelo de criação de uma cluster

```yaml
kind: Cluster
apiVersion: kind.x-k8s.io/v1alpha4
nodes:
  - role: control-plane
  - role: worker
  - role: worker
```

## Adicionando labels nos nodes(nós).

Podemos adicionar labels nos nós(nodes) após a sua criação pela linha de comando.

```
kubectl label nodes codestream-worker region=sa-east-1
```
