<h1> ElysiaAPI <img src="https://github.com/user-attachments/assets/bc6d687c-dd26-4bcd-bcbf-71a8a5681bc3" width="25"/> </h1>

<p>API REST para gestão inteligente de pátios de motocicletas.
Permite gerenciar Motos, Usuários e Vagas com persistência em Oracle e autenticação JWT.<br>

---

## 👥 Integrantes
 
- Iris Tavares Alves 557728 </br>
- Taís Tavares Alves 557553 </br>

---

## ⚙️ Tecnologias

- .NET 9 + .NET 8 WebAPI
- Entity Framework Core
- Oracle
- JWT Bearer
- Swagger / OpenAPI 
- xUnit


---

### ⚠️ Checar versões SDK (garanta que tenha ambas as versões 8 e 9 do SDK instaladas)
> <a href="https://dotnet.microsoft.com/pt-br/download/dotnet/9.0">SDK 9 Download</a>

> <a href="https://dotnet.microsoft.com/en-us/download/dotnet/8.0">SDK 8 Download</a>

### ⚠️ Para testar o Swagger estar na seguinte URL
```text
http://localhost:5243/swagger/index.html
```

---

### 1. Clone o repositório
```text
git clone https://github.com/Irissuu/Csharp_Elysia.git
```

### 2. Restaure dependências
```text
dotnet restore
```

### 3. Coloque suas credenciais e a JWT Key
```text
 "ConnectionStrings": {
    "OracleDB": "User Id=;Password=;Data Source=oracle.fiap.com.br:1521/orcl;"
  },
  "Jwt": {
    "Key": "",
```

### 4. Gere o banco de dados com EF Core
```text
dotnet ef migrations add Inicial
dotnet ef database update
```

### 5. Execute o projeto
```text
dotnet run
```

---

## 🔁 Rotas Disponíveis (via Swagger)

### AuthController

| Método | Rota              | Descrição           |
|--------|-------------------|---------------------|
| POST   | `/api/v1/auth/login` | Faz login e gera JWT |


### MotoController

| Método | Rota                                    | Descrição                       |
|--------|-----------------------------------------|----------------------------------|
| GET    | `/api/v1/motos`                         | Lista todas as motos             |
| GET    | `/api/v1/motos/{id}`                    | Busca uma moto por ID            |
| GET    | `/api/v1/motos/search?placa=XXX`        | Busca moto por placa (parcial)   |
| POST   | `/api/v1/motos`                         | Cadastra uma nova moto           |
| PUT    | `/api/v1/motos/{id}`                    | Atualiza uma moto existente      |
| DELETE | `/api/v1/motos/{id}`                    | Remove uma moto                  |


### UsuarioController

| Método | Rota                         | Descrição                 |
|--------|------------------------------|----------------------------|
| GET    | `/api/v1/usuarios/{id}`      | Busca um usuário por ID    |
| POST   | `/api/v1/usuarios`           | Cria um usuário            |
| PUT    | `/api/v1/usuarios/{id}`      | Atualiza um usuário        |
| DELETE | `/api/v1/usuarios/{id}`      | Remove um usuário          |


### VagaController

| Método | Rota                         | Descrição                 |
|--------|------------------------------|----------------------------|
| GET    | `/api/v1/vagas`              | Lista todas as vagas       |
| GET    | `/api/v1/vagas/{id}`         | Busca uma vaga por ID      |
| GET    | `/api/v1/vagas/patio?patio=XYZ` | Lista vagas por pátio   |
| POST   | `/api/v1/vagas`              | Cadastra uma nova vaga     |
| PUT    | `/api/v1/vagas/{id}`         | Atualiza uma vaga          |
| DELETE | `/api/v1/vagas/{id}`         | Remove uma vaga            |


---
## 📧 Testes Swagger 

## ⋆˚꩜｡ USUARIO
### POST /api/v1/usuarios
```text
{
  "nome": "Maria Eduarda Silva",
  "cpf": "45879612348",
  "email": "maria@gmail.com",
  "senha": "chokito"
}
```


### POST /api/v1/auth/login
```text
{
  "email": "maria@gmail.com",
  "senha": "chokito"
}
```

### PUT /api/v1/usuarios/{id}
```text
{
  "nome": "Maria Eduarda Silva",
  "email": "maria@gmail.com",
  "senha": "DORITOS"
}
```

## ⋆˚꩜｡ MOTO
### POST /api/v1/motos
```text
{
  "placa": "ABC1D34",
  "marca": "Honda",
  "modelo": "CG 160",
  "ano": 2022
}
```

### PUT /api/v1/motos/{id}
```text
{
  "placa": "ABC1D34",
  "marca": "Honda",
  "modelo": "CG 160 FAN",
  "ano": 2023
}
```

## ⋆˚꩜｡ VAGA
### POST /api/v1/vagas
```text
{
  "patio": "ITAQUERA",
  "codigoVaga": "VAGA-19"
}
```

### PUT /api/v1/vagas/{id}
```text
{
  "patio": "ITAQUERA",
  "codigoVaga": "VAGA-19-B"
}
```
---


## 📧 Testes xUnit

### 1. Entre na pasta de testes
```text
cd ElysiaAPI/ElysiaAPI.Tests
```

### 2. Restaure dependências
```text
dotnet restore
```

### 3. Rodar TODOS os testes
```text
dotnet test
```

---

## 🧾 Consulta no banco Oracle

Para visualizar os dados diretamente no Oracle SQL Developer, use **aspas nos nomes das tabelas**:

```sql
SELECT * FROM "MotoCsharp";
SELECT * FROM "VagaCsharp";
SELECT * FROM "UsuarioCsharp";

