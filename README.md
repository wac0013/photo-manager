# Photo Manager

Este é um projeto que gerencia fotos, organizado em microserviços utilizando sub-módulos Git.

## Estrutura do Projeto

O projeto é composto pelos seguintes sub-módulos:

- `front`: Frontend da aplicação (Vite, React 19, TanStack, Tailwind, Shadcn).
- `user-service`: Microserviço de usuários (NestJS, Prisma 7, Better Auth, Swagger).
- `photo-service`: Microserviço de fotos.
- `infra`: Infraestrutura como código (Terraform).

## Como clonar o projeto

Como o projeto utiliza sub-módulos, você deve clonar utilizando o comando:

```bash
git clone --recursive <url-do-repositorio>
```

Ou, se já clonou:

```bash
git submodule update --init --recursive
```

## Como executar o projeto

Para subir todos os serviços, incluindo as dependências (Redis e Postgres), utilize o Docker Compose:

```bash
docker-compose up -d
```

## Tecnologias Utilizadas

- **Node.js 24**: Ambiente de execução para os serviços.
- **NestJS**: Framework para os microserviços de backend.
- **Vite & React 19**: Tecnologias de frontend.
- **Prisma 7**: ORM para acesso ao banco de dados.
- **Better Auth**: Sistema de autenticação moderno.
- **Redis**: Cache e mensageria.
- **Postgres**: Banco de dados relacional.
- **Docker & Docker Compose**: Orquestração de containers local.
- **Git Submodules**: Gerenciamento de múltiplos repositórios.

## Autenticação (Better Auth)

O projeto está integrado ao Better Auth. Para que a autenticação funcione:

1. O `user-service` atua como o servidor de autenticação.
2. O `front` deve ter a variável de ambiente `VITE_AUTH_URL` apontando para o endpoint do `user-service` (ex: `http://localhost:8080/api/auth`).
3. Configure os provedores (Email/Senha e Google) no `user-service`.
