# Secrets

É um recurso que permite guardar as informações sensíveis da aplicação e que não devem ser expostas. Essas informações podem ser consumidas por sistemas ou em nome de um Pod.

Por default ele não está seguro porque fica em base64 e é fácil remover a máscara.

Os Secrets ficam armazenados no Etcd e não são criptografado e seu acesso é restrito por meio do RBAC(Role Based Access Control) e que permite controlar quais usuários e Pods podem acessar.

Podemos montar os Secrets em Pods na forma de arquivos montados ou criando variáveis de ambientes no container.

Quando um Secret é atualizado, o Kubernetes não atualiza automaticamente os volumes e variáveis e ambientes que fazem referência a eles.

## Tipos de Secrets

Temos alguns tipos de Secrets que podem ser usados dependendo da necessidade específica. São eles:

1. **Opaque Secrets**: Os mais simples e comuns. Armazenam dados arbitrários como chaves de API, senhas e token. No Kubernetes eles são codificados na base64, mas não são criptografados. Não recomendado para armazenar dados extremamente sensíveis, como senhas de Banco de Dados.

2. **kubernetes.io/service-account-token**: Armazenam token de acesso a conta de serviço. Estes token são usados para autenticar Pods com o Kubernetes API. Ele é montado automaticamente em Pods que usam contas de serviço.

3. **kubernetes.io/dockercfg e kubernetes.io/dockerconfigjson**: Usados para armazenar credentiais de acesso ao registro Docker. São montados em Pods que tem acesso ao registro do Docker e que sejam containers de acesso privado.

4. **kubernetes.io/tls, kubernetes.io/ssh-auth e kubernetes.io/basic-auth**: Usados para armazenar certificados TLS, chaves SSH e crediciais e autenticação básica. São usados em Pods que precisam de autenticação em outros serviços.

5. **bootstrap.kubernetes.io/token**: Armazenam token de inicialização de Cluster. Usados para autenticar nodes(nós) no Control Plane do Kubernetes.

## Criando Secrets

Com o arquivo .yaml configurado executados o comando abaixo.

```bash
kubectl apply -f secret-file.yaml
```

Pela linha de comando podemos usar o comandos abaixo.

Para secret do tipo Opaque

```bash
kubectl create secret generic tux-test --from-literal=username=Y29kZXN0cmVhbQ== --from-literal=password=Z2lyb3BvcHM=
```

Para Secret do tipo TLS

```bash
openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout chave-privada.key -out certificado.crt
kubectl create secret tls tls-secret --cert=certificado.crt --key=chave-privada.key
```

## Listando os Secrets

```bash
kubectl get secrets

kubectl get secrets secret-name -o yaml
```

## Detalhes do Secret

```bash
kubectl describe secrets secret-name
```

## Deletando Secret

Para remover usamos o comando abaixo.

```bash
kubectl delete -f file.yaml
```

## Criando um secret base64

Podemos criar secrets com o comando abaixo.

```bash
echo -n "secret" | base64
```
## Descriptando o secret base64

Podemos descobrir o secret através do comando abaixo.

```bash
echo -n "secret-name" | base64 -d
```
