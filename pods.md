# Pod

É a menor unidade de gerenciamento do Kubernetes e pode ter um ou mais containers, ou seja, ele agrupa containers e os containers dentro de um Pod compartilham os recursos deste Pod. Ele cria um isolamento.

É muito importante definir nos Pods o uso de recursos de CPU e memória, por exemplo.

## Listando Pods em execução

Quando queremos obter os pods que temos no nosso cluster, usamos o comando abaixo

```bash
kubectl get pods

kubectl get pods/po -n kube-system -o wide

kubectl get pods/po name-pod -o yaml

kubectl get pods/po -n kube-system

kubectl get pods/po -A

kubectl get pods -L app=nginx-deployment
```

O parâmetro -n é de namespaces do Kubernetes

O parâmetro -o wide exibe mais detalhes na saída.

O parâmetro -A realiza a busca independente de namespaces.

O parâmetro -L realiza a busca pelo label definido durante a criação do Pod.

## Criando um Pod

Criando um Pod.

```bash
kubectl run --image nginx --port 80 phoenix
```

Acessando um Pod durante a sua criação pode ser usado os parâmetros -it que permite interagir e ter um terminal para acessar o container. Para ocorrer esse acesso a imagem precisa deste suporte.

```bash
kubectl run -ti --image alpine name-pod
```

Se precisamos podemos criar um arquivo .yaml usando a opcão --dry-run=client e simular a criação de um pod.

```bash
kubectl run --image nginx --port 80 tux --dry-run=client -o yaml > pod.yaml
```

Com o arquivo gerado, podemos criar definitivamente o pod com o comando abaixo.

```bash
kubectl apply -f pod.yaml
```

## Acessando um Pod

Há algumas formas de interagir com os containers de um Pod.

Quando o Pod já está em execução, podemos acessar com o comando abaixo.

Os parâmetros -c significa qual o nome do container e o -it permite interatividade com um terminal.

```bash
kubectl attach name-pod -c name-container -it
```

## Executando comandos em um Pod

```bash
kubectl exec name-pod -- ls /var/log
```

Quando precisamos acessar um pod com bash ou sh.

```bash
kubectl exec -it tux -- bash
```

## Listando informações do Pod

```bash
kubectl describe pods name-pod
```

## Logs do Pod

```bash
kubectl logs name-pod

kubectl logs name-pod -c name-container

kubectl logs -f name-pod
```

## Removendo Pods

```bash
kubectl delete pods name-pod

kubectl delete -f pod.yaml
```
