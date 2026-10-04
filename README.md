# Desafio: Validação e Segurança

API REST de cidades e eventos com **autenticação OAuth2/JWT**, **controle de acesso por perfil** e **validação de dados**.

Desafio do curso Java Spring Professional da DevSuperior.

## 🛠 Tecnologias

- Java 21
- Spring Boot 3.1
- Spring Security
- OAuth2 Authorization Server e Resource Server (JWT)
- Spring Data JPA
- Bean Validation
- H2 Database
- Maven

## 🔐 Regras de acesso

| Método | Rota | Acesso |
|---|---|---|
| POST | `/oauth2/token` | Público (login) |
| GET | `/cities` | Público |
| GET | `/events` | Público (paginado) |
| POST | `/cities` | ADMIN |
| POST | `/events` | ADMIN ou OPERATOR |

## ✅ Validações

**Cidade**
- Nome: obrigatório

**Evento**
- Nome: obrigatório
- Data: não pode ser passada
- Cidade: obrigatória

Dados inválidos retornam `422 Unprocessable Entity` com a mensagem de cada campo.

## 👤 Usuários de teste

| Usuário | Perfis |
|---|---|
| ana@gmail.com | OPERATOR |
| bob@gmail.com | OPERATOR, ADMIN |

Senha: `[senha do seed]`

## ▶️ Como rodar

```bash
git clone https://github.com/bgarbero/desafio-validacao-seguranca.git
cd desafio-validacao-seguranca
./mvnw spring-boot:run
```

A API sobe em `http://localhost:8080`.

## 🧪 Testando com Postman

Na raiz do projeto há uma collection e um environment do Postman. Importe os dois e:

1. Execute **Login** para gerar o token (client: `[client-id]` / `[client-secret]`)
2. O token é usado automaticamente nas requisições protegidas

---

Feito por [Bruno Garbero](https://www.linkedin.com/in/bruno-garbero/)
