# 📸 Photo Manager

Sistema completo de gerenciamento de fotos organizado em álbuns, com autenticação de usuários e armazenamento em nuvem.

## 🏗️ Arquitetura

O projeto segue uma arquitetura de microserviços, composto por:

```
photo-manager/
├── modules/
│   ├── front/           # Frontend React + Vite
│   ├── user-service/    # Serviço de autenticação (NestJS)
│   ├── photo-service/   # Serviço de fotos/álbuns (NestJS)
│   └── infra/           # Configurações de infraestrutura
├── nginx/               # API Gateway
├── docker-compose.yml   # Orquestração de containers
└── data/                # Dados persistentes (PostgreSQL)
```

## 🚀 Tecnologias

| Módulo | Tecnologias |
|--------|-------------|
| **Frontend** | React 19, Vite, TanStack Router, TanStack Query, Tailwind CSS, shadcn/ui |
| **User Service** | NestJS 11, Prisma, Better Auth, PostgreSQL |
| **Photo Service** | NestJS 11, Prisma, Google Cloud Storage, Sharp |
| **Infraestrutura** | Docker, Nginx, PostgreSQL, Redis |

## 📋 Pré-requisitos

- Node.js 22+
- pnpm ou npm
- Docker e Docker Compose
- Conta no Google Cloud Platform (para armazenamento de imagens)

## 🛠️ Instalação

### 1. Clone o repositório

```bash
git clone git@github.com-personal:wac0013/photo-manager.git
cd photo-manager
```

### 2. Inicie os serviços de infraestrutura

```bash
docker-compose up -d db redis gateway
```

### 3. Configure as variáveis de ambiente

Crie os arquivos `.env` em cada módulo seguindo os exemplos `.env.example`.

### 4. Instale as dependências e execute as migrações

```bash
# User Service
cd modules/user-service
pnpm install
pnpm prisma:migrate
pnpm start:dev

# Photo Service
cd ../photo-service
pnpm install
pnpm prisma:migrate
pnpm start:dev

# Frontend
cd ../front
pnpm install
pnpm dev
```

## 🌐 Portas e Endpoints

| Serviço | Porta | URL |
|---------|-------|-----|
| Frontend | 5173 | http://localhost:5173 |
| User Service | 3000 | http://localhost:3000 |
| Photo Service | 4000 | http://localhost:4000 |
| API Gateway | 8080 | http://localhost:8080 |
| PostgreSQL | 5432 | localhost:5432 |
| Redis | 6379 | localhost:6379 |

## 📖 Documentação das APIs

- **User Service**: http://localhost:3000/docs ou http://localhost:8080/api/users/docs
- **Photo Service**: http://localhost:4000/docs ou http://localhost:8080/api/photos/docs

## 🐳 Docker

### Subir todos os serviços

```bash
docker-compose up -d
```

### Subir apenas infraestrutura

```bash
docker-compose up -d db redis gateway
```

### Verificar logs

```bash
docker-compose logs -f [service-name]
```

## 📁 Estrutura dos Módulos

### Frontend (`modules/front`)
Aplicação React responsável pela interface do usuário.
- Gerenciamento de álbuns e fotos
- Upload de imagens com validação
- Visualização em grid e tabela
- Tema claro/escuro

### User Service (`modules/user-service`)
Serviço de autenticação e gerenciamento de usuários.
- Autenticação via Better Auth
- Gerenciamento de sessões
- Validação de tokens

### Photo Service (`modules/photo-service`)
Serviço de gerenciamento de fotos e álbuns.
- CRUD de álbuns
- Upload e processamento de imagens
- Armazenamento no Google Cloud Storage
- Extração de metadados (cor dominante, dimensões, etc.)

## 🔒 Autenticação

O sistema utiliza **Better Auth** para autenticação, suportando:
- Login com email/senha
- Gerenciamento de sessões
- Tokens JWT

## 📝 Licença

Este projeto é privado e de uso restrito.

## 👤 Autor

**Wellington Costa**
- Email: wac.0013@gmail.com
- GitHub: [@wac0013](https://github.com/wac0013)
