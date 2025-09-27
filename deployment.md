# Deployment

Responsável pela configuração e criação de containers e suas características. É forma recomendada para se criar containers no Kubernetes.

Ele sempre irá criar um **ReplicaSet** para garantir o número de réplicas que for definida no deployment.

## Criando um Deployment

Para criar uma deployment pela linha de comando temos o comando abaixo.

```bash
kubectl create deployment nginx --image nginx --replica 3 nginx-deployment
```

Se precisarmos podemos criar um arquivo .yaml usando a opcão --dry-run=client e simular a criação de um deployment.

```bash
kubectl create deployment --image nginx --port 80 nginx --dry-run=client -o yaml > deployment.yaml
```

Com o arquivo gerado, podemos criar definitivamente o deployment com o comando abaixo.

```bash
kubectl apply -f deployment.yaml
```

## Listando Deployment

Quando queremos listar os deployments que temos no nosso cluster.

```bash
kubectl get deployments.apps/deploy.apps

kubectl get deployment/deploy -n kube-system -o wide

kubectl get deployment/deploy -n kube-system -o yaml

kubectl get deployment/deploy -n kube-system

kubectl get deployment/deploy -A

kubectl get pods -l app=nginx-deployment
```

O parâmetro -n é de namespace

O parâmetro -o wide exibe mais detalhes na saída.

O parâmetro -A realiza a busca independente de namespace

## Listando detalhes do Deployment

Se precisamos listar as informações sobre um determinado Deployment, podemos executar o comando abaixo.

```bash
kubectl describe deployments name-deployment
```

## Exibindo as atualizações

Quando precisamos verificar as atualizações, pode usar o comando abaixo.

```bash
kubectl rollout status deployments -n tux nginx-deployment
```

## Desfazendo alterações

Quando precisamos desfazer alguma alteração feita usamos o rollout.

```bash
kubectl rollout undo deployments -n tux nginx-deployment

kubectl rollout undo deployments -n tux nginx-deployment --to-revision number
```

Para refazer as atualizações usamos o comando abaixo.

```bash
kubectl rollout restart deployments -n tux nginx-deployment
```

Podemos pausar ou iniciar as atualizações executando o comando abaixo.

```bash
kubectl rollout pause deployments -n tux nginx-deployment

kubectl rollout resume deployments -n tux nginx-deployment
```

Podemos verificar o histórico de atualizações feitas executando o comando abaixo.

```bash
kubectl rollout history deployments -n tux nginx-deployment

kubectl rollout history deployments -n tux nginx-deployment --revision number
```

## Escalando o Deployment

Podemos alterar as réplicas do Deployment com o comando abaixo.

```bash
kubectl scale deployments -n tux --replicas 2 nginx-deployment
```

## Removendo Deployments

A remoção de um Deployment ocorre com a execução do comando abaixo.

```bash
kubectl delete deployment name-deployment

kubectl delete -f deployment.yaml
```
