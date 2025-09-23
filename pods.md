# Pod

É a menor unidade de gerenciamento do Kubernetes e pode ter um ou mais containers, ou seja, ele agrupa containers e os containers dentro de um Pod compartilham os recursos deste Pod. Ele cria um isolamento.

É muito importante definir nos Pods o uso de recursos de CPU e memória, por exemplo.

## Listando os Pods em execução

Quando queremos obter os pods que temos no nosso cluster, usamos o comando abaixo

```
kubectl get pods

kubectl get pods/po -n kube-system -o wide

kubectl get pods/po name-pod -o yaml

kubectl get pods/po -n kube-system

kubectl get pods/po -A

kubectl get pods -l app=nginx-deployment
```

O parâmetro -n é de namespaces do Kubernetes

O parâmetro -o wide exibe mais detalhes na saída.

O parâmetro -A realiza a busca independente de namespaces.

O parâmetro -l realiza a busca pelo label definido durante a criação do Pod.

## Criando um Pod

Criando um Pod.

```
kubectl run --image nginx --port 80 giropops
```

Acessando um Pod durante a sua criação pode ser usado os parâmetros -it que permite interagir e ter um terminal para acessar o container. Para ocorrer esse acesso a imagem precisa deste suporte.

```
kubectl run -ti --image alpine name-pod
```

Se precisamos podemos criar um arquivo .yaml usando a opcão --dry-run=client e simular a criação de um pod.

```
kubectl run --image nginx --port 80 giropops --dry-run=client -o yaml > pod.yaml
```

Com o arquivo gerado, podemos criar definitivamente o pod com o comando abaixo.

```
kubectl apply -f pod.yaml
```

## Acessando um Pod

Há algumas formas de interagir com os containers de um Pod.

Quando o Pod já está em execução, podemos acessar com o comando abaixo.

Os parâmetros -c significa qual o nome do container e o -it permite interatividade com um terminal.

```
kubectl attach name-pod -c name-container -it
```

## Executando comandos em um Pod

Executando comando em um Pod.

```
kubectl exec name-pod -- ls /var/log
```

Quando precisamos acessar um pod com bash/sh, os comando abaixo deve ser executado.

```
kubectl exec -it giropops -- bash
```

## Listando as informações do Pod

Obtendo detalhes sobre bre um determinado Pod.

```
kubectl describe pods name-pod
```

## Logs do Pod

Obtendo logs do que ocorreu no Pod.

```
kubectl logs name-pod

kubectl logs -f name-pod
```

## Removendo Pods

Removendo Pods.

```
kubectl delete pods name-pod

kubectl delete -f pod.yaml
```
