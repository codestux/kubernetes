# Control Plane

É o node(nó) responsável pelo controle e gerenciamento do cluster. Ele possui containers com os serviços necessários para fazer esse gerenciamento.

É possível executar aplicações no Control Plane, mas não é recomendado e precisa realizar algumas modificações.

## Componentes do Control Plane

### etcd

É responsável por guardar todas as informações do cluster e é recomendado sempre ter várias réplicas/redundância dele, se o gerenciamento é feito por você, devido a sua importância.

O único componente que se comunica com o etcd é o Kube API Server.

A porta do componente é: 2379/tcp e 2380/tcp

### Kube API Server

Responsável por se comunicar com os outros componentes do cluster. As informações dele são enviadas para o componente etcd.

A porta TCP do componente é: 6443/tcp.

### Kube Scheduler

É um agendador responśavel por executar os comandos enviados pelo Kube API Server. Há comunicação com o Kube API Server.

A porta do componente é: 10251/tcp

### Kube Controller Manager

É o responsável pelo controle/gerenciamento do cluster. Se comunica com o Kube API Server.

A porta do componente é: 10252/tcp.
