# Integração do Helm ao Azure DevOps

Neste guia, vamos abordar como integrar o Helm ao Azure DevOps para automatizar o processo de implantação de aplicativos Kubernetes usando charts Helm.

## Passo 1: Configurar um Repositório Git

Certifique-se de ter um repositório Git que contenha seus charts Helm. Você pode usar qualquer provedor de Git, como GitHub, Azure Repos, GitLab, etc.

## Passo 2: Criar um Pipeline no Azure DevOps

1. Acesse o [Azure DevOps](https://dev.azure.com) e vá para a sua organização e projeto.
2. No menu do lado esquerdo, clique em "Pipelines" e depois em "Pipelines".
3. Clique em "New Pipeline" para criar um novo pipeline.

## Passo 3: Configurar a Origem do Pipeline

1. Selecione o repositório Git onde seus charts Helm estão armazenados.
2. Escolha a branch e o caminho do arquivo YAML do pipeline, geralmente é o diretório raiz do repositório.

## Passo 4: Escrever o Arquivo de Pipeline

Você precisará escrever um arquivo YAML do pipeline que execute os comandos Helm para implantar seu aplicativo no Kubernetes. Aqui está um exemplo:

```yaml
trigger:
- master

pool:
  vmImage: 'ubuntu-latest'

steps:
- task: HelmInstaller@1
  inputs:
    helmVersionToInstall: 'latest'

- script: |
    helm repo add meu-repo https://meu-repo.com
    helm repo update
    helm upgrade --install meu-aplicativo meu-repo/meu-chart
  displayName: 'Deploy usando Helm'
```
## Passo 5: Executar o Pipeline

1. Salve as alterações no arquivo YAML do pipeline. 
2. Execute o pipeline para implantar seu aplicativo Kubernetes usando o Helm.

## Passo 6: Adicionar Variáveis de Ambiente (Opcional)

Se o seu processo de implantação depender de valores específicos do ambiente, você pode adicionar variáveis de ambiente no Azure DevOps e usá-las no seu arquivo YAML do pipeline.

## Passo 7: Configurar Gatilhos de Implantação (Opcional)

Você pode configurar gatilhos de implantação para acionar a implantação automaticamente sempre que houver uma alteração no repositório Git.

## Passo 8: Executar Testes Automatizados

É uma prática recomendada executar testes automatizados, como testes de unidade e testes de integração, como parte do processo de CI/CD.

##  Passo 6: Monitoramento e Logging

Configure o monitoramento e logging adequados para o seu aplicativo Kubernetes para garantir que você possa identificar e solucionar problemas rapidamente.

## Vídeo de suporte
https://www.youtube.com/watch?v=4U7ejCffUZs&t=10s
