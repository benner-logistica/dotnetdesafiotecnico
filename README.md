# Desafio Técnico Fullstack - .NET Core + React

Este repositório contém a estrutura inicial de um projeto full stack com back-end em ASP.NET Core (.NET 8) usando Clean Architecture e front-end em React com TailwindCSS.
---

## 📝 Descrição
Crie uma aplicação web de gerenciamento de tarefas (To-Do List) com API em **.NET Core** e front-end em **React**.
---

## 🔧 Pré-requisitos

- [.NET 8 SDK](https://dotnet.microsoft.com/)
- [Node.js](https://nodejs.org/)
- [Docker](https://www.docker.com/) (opcional, para ambiente com docker-compose)
---
---

## 🎯 Objetivos

### 📌 Back-End (.NET Core)
- Criar API RESTful com as seguintes rotas:
  - `POST /login`: autenticação JWT
  - `GET /tasks`: listar todas as tarefas do usuário logado
  - `GET /tasks/{id}`: obter uma tarefa específica
  - `POST /tasks`: criar nova tarefa
  - `PUT /tasks/{id}`: atualizar uma tarefa
  - `DELETE /tasks/{id}`: excluir tarefa

### 🗂️ Modelo de Dados
```csharp
public class TaskItem
{
    public Guid Id { get; set; }
    public string Title { get; set; }
    public string Description { get; set; }
    public DateTime DueDate { get; set; }
    public bool IsCompleted { get; set; }
}
```

### 🔐 Requisitos Técnicos Backend
- Autenticação JWT
- Clean Architecture (Domain, Application, Infrastructure, WebApi)
- Entity Framework Core com SQLite (ou outro banco à escolha)
- Validações com FluentValidation
- Swagger para documentação da API
- **Testes automatizados com xUnit ou NUnit**
  - Cobertura mínima recomendada: serviços e controladores principais
  - Mock de repositórios com Moq ou equivalente

---
### 💻 Front-End (React)
- Página de login
- Página principal com lista de tarefas (filtro por status: todas, pendentes, concluídas)
- Formulário para criação e edição de tarefas
- Botões de ação (editar, concluir, excluir)

### 💡 Requisitos Técnicos Frontend
- React com Vite (ou Create React App)
- Hooks e Context API, Redux ou zustand
- Axios ou fetch para chamadas HTTP
- TailwindCSS, MUI ou outro framework de UI (opcional)
- **Testes automatizados com Jest + Testing Library**
  - Testar componentes de formulário e tela de login
  - Testes de integração simulando chamadas à API com mocks

---
## 📦 Entregáveis
- Repositório GitHub com:
  - Código-fonte completo
  - README com instruções para rodar API e front-end
  - Explicações técnicas (ex: decisões de arquitetura)
- Opcional: docker-compose para facilitar execução local

---
## ✅ Critérios de Avaliação

| Critério                     | Peso |
|-----------------------------|------|
| Organização do código       | ⭐⭐⭐⭐ |
| Boas práticas e arquitetura | ⭐⭐⭐⭐ |
| Funcionamento da aplicação  | ⭐⭐⭐⭐ |
| Validação e autenticação    | ⭐⭐⭐ |
| UI e UX do front-end        | ⭐⭐  |
| Uso de Git (commits claros) | ⭐⭐  |
| **Testes automatizados**    | ⭐⭐  |

---
## ⏱️ Tempo estimado
3 a 5 dias úteis

---
## ⚙️ Starters

### 🧱 Estrutura Backend (Clean Architecture)
```
Backend/
├── src/
│   ├── TaskManager.WebApi         # Camada de apresentação
│   ├── TaskManager.Application    # Regras de negócio
│   ├── TaskManager.Domain         # Entidades e interfaces
│   └── TaskManager.Infrastructure # Repositórios e banco
├── tests/
│   └── TaskManager.Tests          # Testes unitários e de integração
├── TaskManager.sln
└── docker-compose.yml             # Banco e WebApi
```

### 🖥️ Estrutura Frontend (React + Tailwind)
```
Frontend/
├── public/
├── src/
│   ├── components/        # Componentes reutilizáveis
│   ├── pages/             # Login, Dashboard
│   ├── services/          # API (axios)
│   ├── context/           # Autenticação e tarefas
│   └── App.tsx
├── tests/                 # Testes unitários dos componentes
├── tailwind.config.js
├── vite.config.ts
└── package.json
```

### 🐳 docker-compose básico
```yaml
version: '3.8'
services:
  api:
    build: ./Backend
    ports:
      - "5000:80"
    depends_on:
      - db
  db:
    image: postgres
    environment:
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: password
      POSTGRES_DB: taskmanager
    ports:
      - "5432:5432"
  frontend:
    build: ./Frontend
    ports:
      - "3000:3000"
```

---
**Bônus:** testes automatizados, CI/CD, deploy no Vercel/Render/Azure.


## ▶️ Como rodar o projeto

### 🔙 Backend (.NET Core)

1. Navegue até a pasta:

```bash
cd Backend/src/TaskManager.WebApi
```

2. Execute as migrações (caso use EF Core):

```bash
dotnet ef database update
```

3. Inicie a API:

```bash
dotnet run
```

A API estará disponível em `http://localhost:5000`.

---

### 💻 Frontend (React)

1. Navegue até a pasta:

```bash
cd Frontend
```

2. Instale as dependências:

```bash
npm install
```

3. Inicie a aplicação:

```bash
npm run dev
```

A interface estará disponível em `http://localhost:3000`.

---

### 🐳 Usando Docker Compose

1. Na raiz do projeto, execute:

```bash
docker-compose up --build
```

Isso irá iniciar a API, banco de dados e o front-end.

---

## 📁 Estrutura

```
DesafioFullstack/
├── Backend/
│   ├── src/
│   ├── tests/
│   └── docker-compose.yml
└── Frontend/
```

---

## 📌 Observações

- Utilize o token JWT retornado pelo login para autenticar as requisições às rotas protegidas.
- Arquivos de exemplo e componentes mockados estão incluídos para facilitar o desenvolvimento.

---

## ✅ Pronto para começar!

Boa sorte no desafio! 💪
