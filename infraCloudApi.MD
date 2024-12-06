# Arquitetura Cloud Multi-AZ

## Sumário
- [Componentes Principais](#componentes-principais)
- [Microserviços](#microserviços)
- [Segurança](#segurança)
- [Cache & Performance](#cache--performance)
- [Observabilidade](#observabilidade)
- [Observações Gerais](#observações-gerais)

## Componentes Principais

### API Gateway & Gerenciamento
- Controle de acessos e conexões
- Documentação de APIs
- Load balancer integrado

## Microserviços

### Auth Service
- Gestão de autenticação
- JWT implementado
- Controle de acesso

### Cart Service
- Gestão de carrinho

### Checkout Service
- Processamento de pagamentos

### Catalog Service
- Gerenciamento de produtos

### Order Service
- Gestão de pedidos

### Notification Service
- Azure Service Bus integrado
- Service Bus Topics

## Segurança

### Controle de Acesso
- Restrições de IP
- Conexões via CDN
- Proteção WAF
- JWT Auth

## Cache & Performance

### Sistema de Cache
- CDN/Static Cache
- Azure Front Door
- Load Balancing

## Observabilidade

### Monitoramento
- Monitoramento de APIs
- Métricas distribuídas
- Logs centralizados

## Observações Gerais

### Integrações
- Conexões internas via API Gateway
- Proteção em rotas críticas
- Cache distribuído

---
