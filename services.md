# Services

São as configurações para que os Pods possam ser expostos, ou seja, será dado permissão para acessos externos aos Pods, inclusive, acesso fora do Cluster.

Ele define o conjunto lógico de Pods e uma política para acessá-los. Permite expor os Pods para acesso por outros Pods, independente de onde estejam sendo executados no Cluster.

Para o Pod ser exposto precisamos criar endpoints que são os IP que permitem o acesso ao recurso disponível nos Pods.

O Services precisam das labels definidas para saber redirecionar o recurso que será exposto.

Os Services são definidos por uma API Kubernetes por meio de um arquivo de manifesto .yaml.

## Tipos de Services

Existem 04 tipos de Services, são eles:

## ClusterIP(padrão)

Expõe o Service em um IP interno do Cluster. Dessa forma, o Service fica acessível apenas dentro do Cluster e os Pods podem acessar.

## NodePort

Expõe o Service na mesma porta de cada Node selecionado no cluster usando NAT. Torna-o acessível para fora do Cluster usando:.

Ele vincula as portas dos containers ao serviço. As portas deste serviços são altas. Estão entre a 30000/tcp e 32676/tcp.

## LoadBalancer

Cria um balanceador de carga externo no ambiente de nuvem atual(se suportado), e atribui um IP fixo, externo ao Cluster, ao Service.

## ExternalName

Mapeia o Service para o conteúdo do campo ExternalName, exemplo, codestream.com.br, retornando um registro CNAME com seu valor.

## Criando um serviço

Criando um Service pela linha de comando.

```bash
kubectl expose pods tux

kubectl expose deployment tux --type NodePort

kubectl expose deployment tux --type LoadBalancer

kubectl create service externalname db-code --external-name db.code.com.br
```

Podemos criar um serviço baseado em outro serviço.

```bash
kubectl expose services --name test nginx --type NodePort
```

O expose informa que queremos expor o componente.

O parâmetro --type informa o tipo de serviço que estamos criando

## Listando Services

```bash
kubectl get service/svc -n kube-system -o wide

kubectl get service/svc -n kube-system

kubectl get service/svc -A
```

O parâmetro -n é de namespace

O parâmetro -o wide exibe mais detalhes na saída.

O parâmetro -A realiza a busca independente de namespace

## Detalhes do Services

```bash
kubectl describe services service-name
```

## Listando Endpoints

```bash
kubectl get endpoints
```

## Headless Service

Cria um serviço que permite acessar os Pods individualmente por seu hostname, por exemplo. Quando configuramos o Headless estamos informando que os Pods não terão um IP de acesso.

### Acessando um Pod

Como o serviço Headless configurado podemos acessar o Pod pelo endereço.

```bash
curl nginx-0.nginx.default.svc.cluster.local
```

## Deletando Services

```bash
kubectl delete services/svc service-name
```

## Serviços nos nós

### Weave Net

A porta do serviço são: 6783/tcp e 6784/udp
