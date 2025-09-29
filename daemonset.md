# DaemonSet

É o componente que garante que pelo menos uma réplica de um Pod seja executado em todos os nodes(nós) do cluster.

## Criando um DaemonSet

Como um arquivo .yaml é possível realizar a criação de um DaemonSet.

```bash
kubectl apply -f name-daemonset.yaml
```

## Listando os DaemonSets

Para listar os DaemonSets criados usamos o comando abaixo.

```bash
kubectl get daemonsets

kubectl get ds
```

## Detalhes do DaemonSets

```bash
kubectl describe daemonsets daemonset-name

kubectl describe ds daemonset-name
```

## Removendo DaemonSet

Como um arquivo .yaml é possível realizar a criação de um DaemonSet.

```bash
kubectl delete -f name-daemonset.yaml
```
