# Sistema de Gestão de Oficina Mecânica - Portugal

Um sistema completo de gestão para oficinas mecânicas no mercado português, desenvolvido com tecnologias modernas.

## 📋 Módulos Principais

### 1. **Agendamentos**
- ✅ Agendamento sem necessidade de cadastro prévio
- ✅ Consulta de disponibilidade
- ✅ Confirmação automática por email/SMS
- ✅ Lembretes de agendamento

### 2. **Gestão de Clientes**
- ✅ Cadastro completo de clientes
- ✅ Histórico de serviços
- ✅ Dados de contacto
- ✅ Preferências de comunicação

### 3. **Gestão de Veículos**
- ✅ Registo de veículos por cliente
- ✅ Histórico de manutenção
- ✅ Dados técnicos do veículo
- ✅ Alertas de manutenção preventiva

### 4. **Orçamentos**
- ✅ Geração de orçamentos detalhados
- ✅ Cálculo automático de custos
- ✅ Aprovação de orçamentos
- ✅ Histórico de orçamentos

### 5. **Ordem de Serviço**
- ✅ Criação de ordens de serviço
- ✅ Atribuição de mecânicos
- ✅ Rastreamento de progresso
- ✅ Notas técnicas

### 6. **Caixa/Faturação**
- ✅ Faturação de serviços finalizados
- ✅ Emissão de recibos e faturas
- ✅ Histórico de transações
- ✅ Relatórios de caixa

### 7. **Financeira**
- ✅ Gestão de pagamentos
- ✅ Contas a pagar (fornecedores)
- ✅ Salários de funcionários
- ✅ Relatórios financeiros
- ✅ Fluxo de caixa

### 8. **Estoque**
- ✅ Gestão de peças e consumíveis
- ✅ Controle de inventário
- ✅ Alertas de estoque mínimo
- ✅ Histórico de movimentações

### 9. **Cadastro de Fornecedores**
- ✅ Dados completos de fornecedores
- ✅ Histórico de compras
- ✅ Condições comerciais
- ✅ Contactos

### 10. **Configuração**
- ✅ Dados da empresa
- ✅ Cadastro de funcionários
- ✅ Parametrizações do sistema
- ✅ Backup e segurança

## 🛠️ Tecnologias

- **Backend**: Node.js + Express
- **Banco de Dados**: PostgreSQL
- **Frontend**: React + TypeScript
- **Autenticação**: JWT
- **API**: RESTful
- **Documentação**: Swagger/OpenAPI

## 📁 Estrutura do Projeto

```
oficina-mecanica-pt/
├── backend/
│   ├── src/
│   │   ├── modules/
│   │   ├── controllers/
│   │   ├── services/
│   │   ├── models/
│   │   ├── routes/
│   │   ├── middleware/
│   │   └── utils/
│   ├── database/
│   │   ├── migrations/
│   │   └── seeds/
│   └── tests/
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── contexts/
│   │   └── utils/
│   └── public/
├── docs/
├── .env.example
├── docker-compose.yml
└── package.json
```

## 🚀 Como Começar

### Pré-requisitos
- Node.js >= 16.0
- PostgreSQL >= 12
- npm ou yarn

### Instalação

1. Clone o repositório
```bash
git clone https://github.com/devpt2026-droid/oficina-mecanica-pt.git
cd oficina-mecanica-pt
```

2. Instale dependências do backend
```bash
cd backend
npm install
```

3. Instale dependências do frontend
```bash
cd ../frontend
npm install
```

4. Configure o arquivo .env
```bash
cp ../.env.example ../.env
```

5. Configure o banco de dados
```bash
cd ../backend
npm run db:migrate
npm run db:seed
```

6. Inicie o servidor
```bash
npm run dev
```

7. Em outro terminal, inicie o frontend
```bash
cd ../frontend
npm start
```

## 📚 Documentação

- [Especificações de Módulos](docs/modulos.md)
- [API Documentation](docs/api.md)
- [Banco de Dados](docs/database.md)
- [Guia de Instalação](docs/instalacao.md)

## 👥 Autores

- Desenvolvido para o mercado português

## 📝 Licença

MIT License - veja LICENSE.md para detalhes

## 📞 Suporte

Para questões e sugestões, abra uma issue no repositório.

---

**Versão**: 1.0.0  
**Data**: 2026-06-10  
**Status**: Em Desenvolvimento 🚀
