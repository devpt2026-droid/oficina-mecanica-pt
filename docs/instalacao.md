# 🔧 Guia de Instalação e Configuração

## Pré-requisitos

- Node.js >= 16.0
- npm >= 8.0
- PostgreSQL >= 12
- Docker e Docker Compose (opcional)
- Git

## Instalação Local

### 1. Clonar o Repositório

```bash
git clone https://github.com/devpt2026-droid/oficina-mecanica-pt.git
cd oficina-mecanica-pt
```

### 2. Configurar Variáveis de Ambiente

```bash
cp .env.example .env
```

Editar `.env` com suas configurações:

```env
# Database
DB_HOST=localhost
DB_PORT=5432
DB_USER=oficina
DB_PASSWORD=sua-senha-segura
DB_NAME=oficina_mecanica

# Backend
NODE_ENV=development
PORT=3000
JWT_SECRET=seu-secret-key-muito-seguro

# Frontend
FRONTEND_URL=http://localhost:3001

# Email (opcional)
SMTP_HOST=smtp.gmail.com
SMTP_USER=seu-email@gmail.com
SMTP_PASSWORD=sua-senha-de-app

# IVA Portugal
IVA_STANDARD=23
```

### 3. Instalar Dependências

#### Backend

```bash
cd backend
npm install
cd ..
```

#### Frontend

```bash
cd frontend
npm install
cd ..
```

### 4. Configurar Banco de Dados

#### Criar Banco de Dados

```bash
createdb -U postgres oficina_mecanica
```

#### Executar Migrações

```bash
cd backend
npm run db:migrate
npm run db:seed
cd ..
```

### 5. Iniciar Aplicação

#### Terminal 1 - Backend

```bash
cd backend
npm run dev
```

Backend estará disponível em: **http://localhost:3000**

#### Terminal 2 - Frontend

```bash
cd frontend
npm start
```

Frontend estará disponível em: **http://localhost:3001**

## Instalação com Docker

### 1. Construir e Iniciar

```bash
docker-compose up -d
```

### 2. Executar Migrações

```bash
docker-compose exec backend npm run db:migrate
docker-compose exec backend npm run db:seed
```

### 3. Acessar Aplicação

- Frontend: **http://localhost:3001**
- Backend API: **http://localhost:3000/api**
- Banco de Dados: **localhost:5432**

### 4. Parar Containers

```bash
docker-compose down
```

## Primeiro Acesso

### Usuário Padrão

- **Email**: admin@oficina.pt
- **Senha**: admin123

> ⚠️ **IMPORTANTE**: Altere a senha no primeiro acesso!

## Estrutura de Pastas

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
│   │   ├── config/
│   │   └── server.js
│   ├── database/
│   │   ├── migrations/
│   │   └── seeds/
│   ├── package.json
│   ├── Dockerfile
│   └── README.md
├── frontend/
│   ├── src/
│   │   ├── components/
│   │   ├── pages/
│   │   ├── services/
│   │   ├── hooks/
│   │   ├── contexts/
│   │   ├── types/
│   │   ├── styles/
│   │   ├── App.tsx
│   │   └── index.tsx
│   ├── public/
│   ├── package.json
│   ├── Dockerfile
│   └── README.md
├── docs/
│   ├── modulos.md
│   ├── database.md
│   └── instalacao.md
├── .env.example
├── docker-compose.yml
├── package.json
├── .gitignore
├── LICENSE
└── README.md
```

## Troubleshooting

### Erro de Conexão ao Banco de Dados

```bash
# Verificar se PostgreSQL está rodando
pg_isready -h localhost -p 5432

# Conectar ao banco
psql -U oficina -h localhost -d oficina_mecanica
```

### Porta Já em Uso

```bash
# Backend (porta 3000)
lsof -i :3000
kill -9 <PID>

# Frontend (porta 3001)
lsof -i :3001
kill -9 <PID>
```

### Limpar Cache Node

```bash
rm -rf node_modules package-lock.json
npm install
```

### Reiniciar do Zero

```bash
# Remover containers
docker-compose down -v

# Remover banco de dados
dropdb -U postgres oficina_mecanica

# Reconstruir
docker-compose up -d
```

## Variáveis de Ambiente Avançadas

```env
# Logging
LOG_LEVEL=debug

# Rate Limiting
RATE_LIMIT_WINDOW_MS=900000
RATE_LIMIT_MAX_REQUESTS=100

# Arquivo
FILE_UPLOAD_DIR=./uploads
MAX_FILE_SIZE=10485760

# Session
SESSION_SECRET=seu-session-secret-super-seguro

# SMS (Twilio)
TWILIO_ACCOUNT_SID=seu-account-sid
TWILIO_AUTH_TOKEN=seu-auth-token
TWILIO_PHONE_NUMBER=+351XXXXXXXXX

# Moeda
CURRENCY=EUR
CURRENCY_SYMBOL=€
DECIMAL_PLACES=2
```

## Próximos Passos

1. ✅ Consultar [Documentação de Módulos](modulos.md)
2. ✅ Configurar dados da empresa
3. ✅ Criar usuários e permissões
4. ✅ Configurar email e SMS
5. ✅ Importar dados (clientes, veículos)
6. ✅ Realizar primeiro agendamento

---

**Versão**: 1.0.0  
**Data**: 2026-06-10
