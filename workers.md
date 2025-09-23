# Workers

É o node(nó) responsável pela execução dos containers das aplicações, ou sejam, dos Pods.

## Componentes do Workers

### Kubelet

Ele é o agente que está presente em todo e qualquer nó do Kubernetes. Ele se comunica com o Kube API Server e informa se está tudo funcionando nos containers.

Este componente pode existe no node(nó) Control Plane.

A porta do componente é: 10250/tcp.

### Kube Proxy

Responsável pela exposição do container no nosso cluster.
