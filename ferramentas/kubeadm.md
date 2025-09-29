# Kubeadm

O responsável pelo criação do Cluster Kubernetes.

## Instalação

Devemos instalar os pacotes abaixo.

```bash
sudo apt-get install -y apt-transport-https ca-certificates curl gpg
```

Em seguida realizamos a configuração da chave pública do repositório Kubernetes.

```bash
curl -fsSL https://pkgs.k8s.io/core:/stable:/v1.30/deb/Release.key | sudo gpg --dearmor -o /etc/apt/keyrings/kubernetes-apt-keyring.gpg
```

Agora, iremos configurar os nosso repositório.

```bash
echo 'deb [signed-by=/etc/apt/keyrings/kubernetes-apt-keyring.gpg] https://pkgs.k8s.io/core:/stable:/v1.30/deb/ /' | sudo tee /etc/apt/sources.list.d/kubernetes.list
```

E finalizamos realizando os procedimentos abaixo.

```bash
sudo apt-get update && sudo apt-get install -y kubelet kubeadm kubectl && sudo apt-mark hold kubelet kubeadm kubectl
```

Antes de inicializar os nodes precisamos nos certificar de que os pacotes abaixo estão instalados.

```bash
sudo apt install  gnupg lsb-release ca-certificates
```

## Instalando o Container Runtime

### containerd

```bash
sudo install -m 0755 -d /etc/apt/keyrings && sudo curl -fsSL https://download.docker.com/linux/ubuntu/gpg -o /etc/apt/keyrings/docker.asc && sudo chmod a+r /etc/apt/keyrings/docker.asc && echo \
  "deb [arch=$(dpkg --print-architecture) signed-by=/etc/apt/keyrings/docker.asc] https://download.docker.com/linux/ubuntu \
  $(. /etc/os-release && echo "$VERSION_CODENAME") stable" | \
  sudo tee /etc/apt/sources.list.d/docker.list > /dev/null && sudo apt-get update &&  sudo apt install containerd.io
  ```

  ### Alterando o CGroup

  Precisamos colocar true no parâmetro do SystemCgroup do arquivo gerado pelo containerd.

  Gerar o arquivo.

```bash
sudo containerd config default | sudo tee /etc/containerd/config.toml
```

Após a alteração temos que realizar o restart do containerd

```bash
sudo systemctl restart containerd && sudo systemctl status containerd && sudo systemctl enable containerd && sudo systemctl enable --now kubelet
```

## Criando um cluster

Precisamos executar os comandos abaixo na instância que será o Control Plane.

```bash
sudo kubeadm init --pod-network-cidr=10.10.0.0/16 --apiserver-advertise-address=192.168.3.133
```

## Adicionando os outros Nodes

Após o Control Plane está configurado, precisamos adicionar os ostros nodes(nós). Com o comando abaixo que foi copiando das instruções de inicialização do Kubeadm.

```bash
kubeadm join 192.168.3.133:6443 --token z5brgo.dxcawp3qfz38udkb \
	--discovery-token-ca-cert-hash sha256:6a49c101d6cb04c5365528405afeeac9f0e8fbb6cd3c6c70feaa4652cad97d70
```
