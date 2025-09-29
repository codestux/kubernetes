# Probes

São os componentes que monitoram a saúde dos Pods realizando testes.

As Probes devem ser declaradas para cada container que for criado.

## LivenessProbe

Realiza algumas verificações de testes para assegurar que os Pods estão saudáveis. Se os testes falharem, os Pods serão reiniciados constantemente até a correção do problema.

## ReadinessProbe

Realiza a configuração dos Pods para garantir que eles estão prontos para receber requisições externas. Caso tenha problema ele é isolado e não receberá requisões até consertar o problema.

## StartupProbe

Ele será executado apenas uma vez. Responsável por verificar se o Pod foi inicializado corretamente e se está pronto para receber requisições.
