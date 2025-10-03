# StateFulSet

Funcionalidade do Kubernetes que gerencia o Deployment e Scaling de um conjunto de Pod. Ele é configurado para quando precisamos ter garantias de execução no nosso sistema.

Os Deployments e Replicaset são considerados stateless

Os StateFulSet tem uma ligação com os PVC's. Quando criamos um Pod ele cria um PVC para cada Pod.

O StateFulSet funcionam criando uma série de Pods replicados. Cada réplica é uma instância da mesma aplicação que é criada a partir do mesmo spec, mas pode ser diferenciada por um índice persistente, endereços e um hostname que se vincula a sua identidade.

## Criando StateFulSet

```bash
kubectl apply -f statefulset.yaml
```

## Listando StateFulSet

```bash
kubectl get statefulsets
```

## Removendo StateFulSet

```bash
kubectl delete -f statefulset.yaml

kubectl delete statefulset statefulset-name
```
