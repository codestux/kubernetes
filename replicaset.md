# ReplicaSet

O Replicaset é responsável pela criação de Pods.

Não é recomendado, nem boa prática e nem uma boa idéia criar ReplicaSet sem ser a partir de um Deployment.

São os responsáveis por garantir que o número de Pods definidos no Deployment sejam mantidos em execução. Ao criar um Deployment é criado um ReplicaSet que fica responsável pelo Pod que definimos.

Se existir uma mudança de configurações nos Pods e mesmo aplicando a mudança os Pods controlados pelo ReplicaSet sem Deployment só irá atualizar após a remoção dos Pods. Assim, temos a situação de ter Pods com versões diferentes.

## Criando um ReplicaSet

Como um arquivo .yaml é possível realizar a criação de um ReplicaSet.

```bash
kubectl apply -f name-replicaset.yaml
```

## Listando os ReplicaSet

Para listar os ReplicaSet usamos o comando abaixo.

```bash
kubectl get replicaset

kubectl get replicasets

kubectl get rs

kubectl get replicaset/rs -n kube-system -o wide

kubectl get replicaset/rs -n kube-system

kubectl get replicaset/rs -A
```

O parâmetro -n é de namespace

O parâmetro -o wide exibe mais detalhes na saída.

O parâmetro -A realiza a busca independente de namespace

## Detalhes do ReplicaSet

```bash
kubectl describe replicaset replicaset-name

kubectl describe rs replicaset-name
```

## Removendo um ReplicaSet

Como um arquivo .yaml é possível realizar a remoção de um ReplicaSet.

```bash
kubectl delete -f name-replicaset.yaml

kubectl delete replicasets replicaset-name
```
