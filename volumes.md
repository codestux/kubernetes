# Volumes e Storage Class

## Volumes

São diretórios que podem existir dentro de um Pod para armazenar dados, arquivos, imagens, documentos, etc.

Existem dois tipos de Volumes no Kubernetes, são eles: Ephemeral Volumes e Persistent Volumes

## Ephemeral Volumes

São volumes que são destruídos junto com o Pod, ou seja, os dados não são persistentes. Se ocorrer problema com o Pod e precisarmos remover, os Ephemeral Volumes serão removidos também e seus dados perdidos.

O emptyDir é um exemplo de volume do tipo Ephemeral Volume.

## Empty Dir

Este volume persiste os dados mesmo se o Pod for restartado, mas se ele for deletado, os dados são permanentemente removidos.

## Persistent Volumes

São volumes que não são removidos e que mantêm os dados armazenados mesmo que o Pod seja destruído por algum motivo.

## Storage Class

É um objeto que descreve e define diferentes classes de armazenamento disponíveis no cluster, ou seja, possibilita que seja feita a configuração por tipos de categorias de volumes de armazenamentos.

O StorageClass, através de provisionadores, cria dinamicamente PV's quando requisições são feitas pelos PVC's.

## Criando um Storage Class

Com o arquivo .yaml das configurações do Storage Class executamos o comando abaixo.

```bash
kubectl apply -f storage-class.yaml
```

## Listando Storage Class

Para listarmos os provisioner do Kind podemos executar o comando abaixo.

```bash
kubectl get storageclass/sc

kubectl get sc
```

## Detalhes do Storage Class

```bash
kubectl describe storageclass/sc
```

## Persistent Volumes

Os Persistent Volumes(PV) são os responsáveis por disponibilizar blocos de armazenamentos necessários para quando o PVC(Persistent Volumes Claim) solicitar.

São objetos responsáveis por criar recursos de armazenamento físico no cluster. Estes armazenamentos podem ser um disco rigido, um serviços de NAS ou armazenamentos em nuvem.

Eles podem usar armazenamentos locais ou em rede.

## Criando Persistent Volume

Como o arquivo .yaml configurado executamos o comando abaixo.

```bash
kubectl apply -f pv-name.yaml
```

## Listando PV

```bash
kubectl get pv

kubectl get persistentvolumes
```

## Detalhes do PV

```bash
kubectl describe pv pv-name
```

## Removendo PV

```bash
kubectl delete pv pv-name
```

## Persistent Volumes Claim

O Persistent Volumes Claim(PVC) é a forma de requisição para o Storage Class ou Persistent Volumes(PV) para que um espaço/storage possa ser disponibilizado para uso.

## Criando Persistent Volumes Claim

Como o arquivo .yaml configurado executamos o comando abaixo.

```bash
kubectl apply -f pvc-name.yaml
```

## Listando PVC

```bash
kubectl get pvc
```

## Removendo PVC

```bash
kubectl delete pvc pvc-name
```
