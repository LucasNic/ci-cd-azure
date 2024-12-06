# Pipeline CI/CD

## Sumário
- [Visão Geral do Pipeline](#visão-geral-do-pipeline)
- [Processo de Rollback](#processo-de-rollback)
- [Observabilidade](#observabilidade)
- [Controles de Produção](#controles-de-produção)
- [Testes de Performance](#testes-de-performance)

## Visão Geral do Pipeline

### Gatilhos de Início
- Manual
- Automático (CI) via commit em Development

### Estágios

#### 1. Build
- Execução em ambiente Docker isolado

#### 2. Testes
- Testes unitários
- Testes de integração

#### 3. Segurança
- CVE scan
- Quality Gate

#### 4. Deploy
- Push para Registry
- Execução Terraform (init/plan/apply)

#### 5. Validação
- Execução de smoke tests

#### 6. Notificação
- Status enviado via canal dedicado

## Processo de Rollback

### STAGE: Push Image to Registry
1. Remoção da imagem recém enviada
2. Restauração da tag anterior no registro
3. Limpeza do cache local

### STAGE: Terraform APPLY
- Não possui ação automatizada no terraform
- Cenário raro (apenas atualização de imagem em containers)
- Procedimentos:
  1. Executar rollback na imagem do registry
  2. Acionar time de DevOps

### STAGE: Smoke Tests
1. Executar rollback na imagem do registry
2. Realizar novo terraform apply
3. Atualizar containers com imagem anterior

### Requisitos Gerais de Rollback
Todos os processos de rollback devem:
- Gerar logs detalhados
- Notificar equipe via canal dedicado
- Atualizar status no pipeline
- Criar relatório do incidente

## Observabilidade

### Monitoramento
- Logs detalhados
- Notificações automáticas
- Relatórios de incidente

## Controles de Produção

### Governança
- Sistema de múltiplos aprovadores
- Processo de change management
- Plano de rollback documentado
- Backup preventivo
- Avaliação de impacto

## Testes de Performance

### JMeter
- Execução automatizada pós-deploy
- Geração de relatório comparativo entre deploys

---
