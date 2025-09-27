# Strategies

Durante a atualização precisamos, em alguns momentos, ter controle de como será o processo de atualização para evitar que todos os Pods sejam removidos/atualizados de uma única vez e a execução da aplicação seja prejudicada.

## RollingUpdate

Essa estratégia define a quantidade de Pods que serão atualizados de uma única vez, quantidade de Pods que podem existir a mais do que foi informado no arquivo de manifesto.

Aceita a definição de números ou por percentual.

### Exemplo

```yaml
strategy :
  type: RollingUpdate
  rollingUpdate:
    maxSurge: 1
    maxUnavailable: 2
```

## Recreate

Essa estratégia remove todos os Pods e atualiza todos de uma única vez.

### Exemplo

```yaml
strategy :
  type: Recreate
```
