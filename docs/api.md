# API REST - Documentação Completa

## Base URL

```
http://localhost:3000/api
```

## Autenticação

Todas as requisições (exceto login e agendamentos públicos) requerem token JWT no header:

```
Authorization: Bearer seu-token-jwt
```

## Status HTTP

- **200** - OK
- **201** - Criado com sucesso
- **400** - Requisição inválida
- **401** - Não autenticado
- **403** - Não autorizado
- **404** - Não encontrado
- **500** - Erro do servidor

---

## 1. AGENDAMENTOS

### Listar Agendamentos
```http
GET /agendamentos
```

### Criar Agendamento Público (sem cadastro)
```http
POST /agendamentos/publicos
Content-Type: application/json

{
  "cliente_nome": "João Silva",
  "cliente_email": "joao@email.com",
  "cliente_telefone": "912345678",
  "tipo_servico": "Revisão",
  "data_agendamento": "2026-06-15T10:00:00Z",
  "veiculo_matricula": "00-AA-01",
  "observacoes": "Cliente preferencia segunda-feira"
}
```

### Verificar Disponibilidade
```http
GET /agendamentos/disponibilidade?data=2026-06-15
```

### Obter Agendamento
```http
GET /agendamentos/:id
```

### Atualizar Agendamento
```http
PUT /agendamentos/:id
Content-Type: application/json

{
  "data_agendamento": "2026-06-20T14:00:00Z",
  "status": "Confirmado"
}
```

### Cancelar Agendamento
```http
DELETE /agendamentos/:id
```

---

## 2. CLIENTES

### Listar Clientes
```http
GET /clientes
```

### Criar Cliente
```http
POST /clientes
Content-Type: application/json

{
  "nome": "Maria Santos",
  "nif": "123456789",
  "email": "maria@email.com",
  "telefone": "912345678",
  "morada": "Rua Principal",
  "numero": "10",
  "cidade": "Lisboa",
  "codigo_postal": "1000-001",
  "preferencia_contacto": "email"
}
```

### Obter Cliente
```http
GET /clientes/:id
```

### Atualizar Cliente
```http
PUT /clientes/:id
Content-Type: application/json

{
  "email": "novo-email@email.com",
  "telefone": "987654321"
}
```

### Listar Histórico de Serviços
```http
GET /clientes/:id/servicos
```

### Deletar/Arquivar Cliente
```http
DELETE /clientes/:id
```

---

## 3. VEÍCULOS

### Listar Veículos
```http
GET /veiculo
```

### Criar Veículo
```http
POST /veiculo
Content-Type: application/json

{
  "matricula": "00-AA-01",
  "marca": "Toyota",
  "modelo": "Corolla",
  "ano_fabrico": 2020,
  "combustivel": "Gasolina",
  "cilindrada": 1.6,
  "numero_chassis": "ABC123XYZ789",
  "cliente_id": 1,
  "km_atuais": 50000
}
```

### Obter Veículo
```http
GET /veiculo/:id
```

### Atualizar Veículo
```http
PUT /veiculo/:id
Content-Type: application/json

{
  "km_atuais": 51000
}
```

### Obter Histórico de Manutenção
```http
GET /veiculo/:id/historico
```

---

## 4. ORÇAMENTOS

### Listar Orçamentos
```http
GET /orcamentos
```

### Criar Orçamento
```http
POST /orcamentos
Content-Type: application/json

{
  "cliente_id": 1,
  "veiculo_id": 1,
  "descricao": "Revisão completa do veículo",
  "data_emissao": "2026-06-10",
  "validade_dias": 30,
  "itens": [
    {
      "descricao": "Óleo do motor",
      "quantidade": 1,
      "preco_unitario": 45.00,
      "tipo": "peca"
    },
    {
      "descricao": "Mão de obra - Revisão",
      "quantidade": 2,
      "preco_unitario": 50.00,
      "tipo": "mao_obra"
    }
  ]
}
```

### Obter Orçamento
```http
GET /orcamentos/:id
```

### Atualizar Orçamento
```http
PUT /orcamentos/:id
Content-Type: application/json

{
  "descricao": "Descrição atualizada"
}
```

### Aprovar Orçamento
```http
PUT /orcamentos/:id/aprovar
```

### Rejeitar Orçamento
```http
PUT /orcamentos/:id/rejeitar
Content-Type: application/json

{
  "motivo": "Valor muito alto"
}
```

---

## 5. ORDEM DE SERVIÇO

### Listar Ordens de Serviço
```http
GET /ordens-servico
```

### Criar Ordem de Serviço
```http
POST /ordens-servico
Content-Type: application/json

{
  "orcamento_id": 1,
  "cliente_id": 1,
  "veiculo_id": 1,
  "data_inicio": "2026-06-15",
  "data_fim_estimada": "2026-06-16",
  "mecanico_id": 3
}
```

### Obter Ordem de Serviço
```http
GET /ordens-servico/:id
```

### Atualizar Ordem de Serviço
```http
PUT /ordens-servico/:id
Content-Type: application/json

{
  "percentual_conclusao": 50
}
```

### Alterar Status
```http
PUT /ordens-servico/:id/status
Content-Type: application/json

{
  "status": "Em Andamento"
}
```

### Adicionar Nota Técnica
```http
POST /ordens-servico/:id/notas
Content-Type: application/json

{
  "nota": "Encontrado problema adicional no sistema de travões"
}
```

---

## 6. FATURAÇÃO

### Emitir Fatura
```http
POST /faturacao/faturas
Content-Type: application/json

{
  "orden_servico_id": 1,
  "cliente_id": 1,
  "data_emissao": "2026-06-16",
  "subtotal": 145.00,
  "forma_pagamento": "Cartão de Crédito"
}
```

### Emitir Recibo Simplificado
```http
POST /faturacao/recibos
Content-Type: application/json

{
  "cliente_nome": "Cliente Ocasional",
  "valor": 100.00,
  "descricao": "Serviço de reparação"
}
```

### Listar Faturas
```http
GET /faturacao/faturas
```

### Cancelar Fatura
```http
PUT /faturacao/faturas/:id/cancelar
```

---

## 7. CAIXA

### Obter Movimento de Caixa
```http
GET /caixa/movimento?data_inicio=2026-06-01&data_fim=2026-06-30
```

### Obter Fechamento de Caixa
```http
GET /caixa/fechamento?data=2026-06-10
```

### Registar Sangria (Retirada)
```http
POST /caixa/sangria
Content-Type: application/json

{
  "valor": 200.00,
  "motivo": "Retirada para caixa pequeno",
  "responsavel_id": 1
}
```

---

## 8. FINANCEIRA

### Registar Pagamento
```http
POST /financeira/pagamentos
Content-Type: application/json

{
  "tipo": "fornecedor",
  "descricao": "Pagamento Fornecedor X",
  "valor": 500.00,
  "data_pagamento": "2026-06-10",
  "forma_pagamento": "Transferência Bancária",
  "fornecedor_id": 1,
  "referencia_pagamento": "REF123456"
}
```

### Listar Contas a Pagar
```http
GET /financeira/contas-a-pagar
```

### Listar Contas a Receber
```http
GET /financeira/contas-a-receber
```

### Gerar Folha de Pagamento
```http
POST /financeira/folha-pagamento
Content-Type: application/json

{
  "mes": 6,
  "ano": 2026
}
```

### Relatório de Fluxo de Caixa
```http
GET /financeira/relatorio-fluxo?data_inicio=2026-06-01&data_fim=2026-06-30
```

### Relatório de Resultado (P&L)
```http
GET /financeira/relatorio-pl?data_inicio=2026-06-01&data_fim=2026-06-30
```

---

## 9. ESTOQUE

### Listar Produtos
```http
GET /estoque/produtos
```

### Criar Produto
```http
POST /estoque/produtos
Content-Type: application/json

{
  "codigo_interno": "SKU001",
  "codigo_fornecedor": "FORN123",
  "descricao": "Óleo Motor 5W40",
  "categoria": "Óleos",
  "subcategoria": "Motor",
  "preco_custo": 35.00,
  "preco_venda": 45.00,
  "estoque_minimo": 10,
  "fornecedor_id": 1
}
```

### Registar Entrada em Estoque
```http
POST /estoque/entrada
Content-Type: application/json

{
  "produto_id": 1,
  "quantidade": 50,
  "motivo": "Compra a fornecedor",
  "referencia": "NOT123456",
  "lote": "LOTE001",
  "validade": "2027-06-10"
}
```

### Registar Saída em Estoque
```http
POST /estoque/saida
Content-Type: application/json

{
  "produto_id": 1,
  "quantidade": 2,
  "motivo": "Utilizado em OS",
  "referencia": "OS001"
}
```

### Obter Relatório de Estoque
```http
GET /estoque/relatorio
```

### Obter Alertas de Estoque
```http
GET /estoque/alertas
```

---

## 10. FORNECEDORES

### Listar Fornecedores
```http
GET /fornecedores
```

### Criar Fornecedor
```http
POST /fornecedores
Content-Type: application/json

{
  "razao_social": "Peças Auto Ltda",
  "nome_fantasia": "Peças Auto",
  "nif": "987654321",
  "email": "contato@pecasauto.pt",
  "telefone": "219876543",
  "iban": "PT50003300000000000000001",
  "endereco": "Rua do Comércio",
  "cidade": "Porto",
  "prazo_pagamento": 30,
  "desconto_padrao": 5.00
}
```

### Obter Fornecedor
```http
GET /fornecedores/:id
```

### Histórico de Compras
```http
GET /fornecedores/:id/historico
```

---

## 11. CONFIGURAÇÃO

### Obter Dados da Empresa
```http
GET /configuracao/empresa
```

### Atualizar Dados da Empresa
```http
PUT /configuracao/empresa
Content-Type: application/json

{
  "nome_fantasia": "Oficina Silva",
  "razao_social": "Silva Reparações Automóveis Lda",
  "nif": "999999999",
  "email": "info@oficina.pt",
  "telefone": "212345678",
  "endereco": "Rua das Oficinas",
  "cidade": "Lisboa"
}
```

### Listar Funcionários
```http
GET /configuracao/funcionarios
```

### Criar Funcionário
```http
POST /configuracao/funcionarios
Content-Type: application/json

{
  "nome": "João Mecânico",
  "nif": "111111111",
  "email": "joao@oficina.pt",
  "cargo": "mecanico",
  "especialidade": "Motor",
  "salario_base": 1200.00,
  "data_inicio": "2026-01-01"
}
```

### Gerar Backup
```http
POST /configuracao/backup
```

---

**Última Atualização**: 2026-06-10
