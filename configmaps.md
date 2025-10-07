# ConfigMaps

É um recurso semelhante aos Secrets que é usado dentro do Kubernetes para armazenar arquivos de configurações.

Eles não são atualizados automaticamente quando há mudanças nos Secrets.

## Criando um ConfigMap

Pela linha de comando pode criar um ConfigMap.

```bash
kubectl apply -f configmap.yaml

kubectl create configmap nginx-config --from-file nginx.conf
```

## Listando os ConfigMaps

```bash
kubectl get configmaps configmap-name

kubectl get configmaps configmap-name -o yaml

kubectl get cm configmap-name
```

## Detalhes do ConfigMaps

```bash
kubectl describe configmaps configmap-name
```

## Deletando ConfigMaps

```bash
kubectl delete apply -f configmap-name

kubectl delete cm configmap-name

kubectl delete configmaps configmap-name
```
