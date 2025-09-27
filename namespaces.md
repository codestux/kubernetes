# Namespaces

É um recurso do Kubernetes que podemos usar para organizar os componentes que são criados por rótulos ou locais onde foram criados.

## Listando Namespaces

Para lista os namespaces.

```bash
kubectl get namespaces
```

O Kubernetes permite que seja organizados os objetos por meio de namespaces.

- default: Quando não especificado o namespace é nele que o comando será executado.

- kube-system: Onde ocorre o gerenciamento do Kubernetes. Os pods estão localizados neste namespace.

## Criando Namespaces

Para criar um namespace pela linha de comando temos o comando abaixo.

```bash
kubectl create namespace tux
```

Se precisamos podemos criar um arquivo .yaml usando a opcão --dry-run=client e simular a criação de um namespace.

```bash
kubectl create namespace tux --dry-run=client -o yaml > tux.yaml
```

Com o arquivo gerado, podemos criar definitivamente o deployment com o comando abaixo.

```bash
kubectl apply -f tux.yaml
```

## Listando as informações do Namespace

Se precisamos listar as informações sobre um determinado Namespace, podemos executar o comando abaixo.

```
kubectl describe namespaces name-namespace
```

## Removendo Namespaces

A remoção de um Namespace ocorre com a execução do comando abaixo.

```
kubectl delete namespaces tux

kubectl delete -f tux.yaml
```

