# Container Engine e Runtime

## Container Engine

O Container Engine é o responsável por gerenciar as imagens e volumes, por exemplo. Ele é o responsável por garantir que os recursos que os containers estão utilizando está devidamente isolados, a vida do container, storage, rede, etc.

No Kubernetes ele não se comunica com o kernel do OS. A idéia é transformar o container mais parecido com um produto.

Existem outros tipos do container engine, como: Docker, Podman, CRI-O.

## Container Runtime

É o responsável por criar os containers e realizar a comunicação com o kernel do OS. Para que o container possa ser executado nos nós é preciso que se tenha um Container Runtime instalado em cada nó.

Ao executar ferramentas como Docker ou Podman, estamos usando um Container Runtime, ou melhor, o Container Engine está fazendo uso de algum Container Runtime.

### Tipos de Container Runtime

#### Low-Level

São executados diretamente pelo Kernel. Temos runc, crun runsc.

#### High-Level

São executados pelo Container Engine.

O Container Runtime do Docker é o **containerd**.

#### Sandbox e Virtualized

São Container Runtime que são executados pelo Container Engine de forma segura. Temos o gVisor que é um Sandbox e o Kata que é um Virtualized.

## OCI - Open Container Iniciative

Grupo de empresa unidas para criar padrões para os containers. Eles foram os criadores do Container Runtime de Baixo-Nível chamado **runc**.
