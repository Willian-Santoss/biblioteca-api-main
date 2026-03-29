# Biblioteca API – Spring Boot (Back-End)

[![Java](https://img.shields.io/badge/Java-17-007396?logo=openjdk&logoColor=white)](https://www.oracle.com/java/technologies/javase/jdk17-archive-downloads.html)
[![Spring Boot](https://img.shields.io/badge/Spring%20Boot-3.5.11-6DB33F?logo=springboot&logoColor=white)](https://spring.io/projects/spring-boot)
[![Maven](https://img.shields.io/badge/Maven-Wrapper-C71A36?logo=apachemaven&logoColor=white)](https://maven.apache.org/)
[![Status](https://img.shields.io/badge/status-em%20desenvolvimento-0A66C2)](#)
[![Licença](https://img.shields.io/badge/licen%C3%A7a-educacional-lightgrey)](#-licença)

Projeto didático da disciplina de **Desenvolvimento Web Back-End** para construção de uma **API REST de biblioteca universitária** com **Java + Spring Boot + Spring Data JPA + H2**.

---

## 📚 Sumário

- [📌 Sobre o projeto](#-sobre-o-projeto)
- [✨ Objetivos de aprendizagem](#-objetivos-de-aprendizagem)
- [🧰 Tecnologias utilizadas](#-tecnologias-utilizadas)
- [🗂️ Estrutura do projeto](#-estrutura-do-projeto)
- [✅ Pré-requisitos](#-pré-requisitos)
- [🚀 Guia completo no VS Code (passo a passo)](#-guia-completo-no-vs-code-passo-a-passo)
- [🧪 Dados iniciais no H2](#-dados-iniciais-no-h2)
- [🔍 Endpoints da API](#-endpoints-da-api)
- [🧪 Testando no Postman/Insomnia](#-testando-no-postmaninsomnia)
- [🖼️ Screenshots obrigatórias](#-screenshots-obrigatórias)
- [🧯 Solução de problemas comuns](#-solução-de-problemas-comuns)
- [📈 Evolução nas próximas aulas](#-evolução-nas-próximas-aulas)
- [👨‍🏫 Contexto acadêmico](#-contexto-acadêmico)
- [📄 Licença](#-licença)

---

## 📌 Sobre o projeto

A aplicação simula o fluxo real de um sistema back-end:

**Cliente → API REST → Banco de Dados (H2) → Resposta**

Funcionalidades atuais:

- listar livros
- buscar livro por ID
- cadastrar livro
- atualizar livro
- remover livro
- simular empréstimo
- simular devolução
- consultar console H2

---

## ✨ Objetivos de aprendizagem

Ao concluir este laboratório, o(a) aluno(a) será capaz de:

- criar e executar uma API REST com Spring Boot
- aplicar arquitetura em camadas (`controller`, `service`, `repository`, `model`)
- integrar persistência com Spring Data JPA
- usar banco em memória H2 para testes rápidos
- validar endpoints HTTP com ferramentas de API

---

## 🧰 Tecnologias utilizadas

- **Java 17+ (recomendado 17)**
- **Spring Boot 3.5.11**
- **Spring Web**
- **Spring Data JPA**
- **H2 Database (em memória)**
- **Lombok**
- **Spring Boot DevTools**
- **Maven Wrapper** (`mvnw` / `mvnw.cmd`)

---

## 🗂️ Estrutura do projeto

```text
biblioteca-api/
├── README.md
├── HELP.md
├── pom.xml
├── mvnw
├── mvnw.cmd
├── docs/
│   └── screenshots/
│       └── GUIA-SCREENSHOTS.md
├── src/
│   ├── main/
│   │   ├── java/com/facens/biblioteca_api/
│   │   │   ├── BibliotecaApiApplication.java
│   │   │   ├── controller/LivroController.java
│   │   │   ├── service/LivroService.java
│   │   │   ├── repository/LivroRepository.java
│   │   │   └── model/Livro.java
│   │   └── resources/
│   │       ├── application.properties
│   │       └── data.sql
│   └── test/java/com/facens/biblioteca_api/
│       └── BibliotecaApiApplicationTests.java
└── target/
```

---

## ✅ Pré-requisitos

Antes de começar:

1. **VS Code**
2. **JDK 17**
3. Extensões do VS Code:
   - **Extension Pack for Java**
   - **Spring Boot Extension Pack**
4. **Git** (opcional, recomendado)

Verifique Java no terminal:

```bash
java -version
```

Saída esperada: versão **17**.

---

## 🚀 Guia completo no VS Code (passo a passo)

### 1) Criar o projeto Spring Boot

1. Abra o VS Code.
2. Pressione `Ctrl + Shift + P`.
3. Execute: **Spring Initializr: Create a Maven Project**.
4. Use as opções:
   - **Language**: Java
   - **Spring Boot**: `3.5.11` (ou próxima disponível)
   - **Group Id**: `com.facens`
   - **Artifact Id**: `biblioteca-api`
   - **Packaging**: `Jar`
   - **Java**: `17`
5. Dependências:
   - Spring Web
   - Spring Boot DevTools
   - Lombok
   - Spring Data JPA
   - H2 Database

### 2) Organizar arquitetura em camadas

Criar os pacotes em `src/main/java/com/facens/biblioteca_api/`:

- `controller`
- `service`
- `repository`
- `model`

### 3) Configurar H2 no `application.properties`

Configurar:

- URL: `jdbc:h2:mem:biblioteca`
- usuário: `sa`
- senha: *(vazia)*
- console H2 habilitado em `/h2-console`
- criação automática de esquema com JPA

### 4) Criar modelo da entidade `Livro`

Campos utilizados:

- `id`
- `titulo`
- `autor`
- `emprestado`
- `dataEmprestimo`

### 5) Criar `LivroRepository`

Interface estendendo `JpaRepository<Livro, Long>`.

### 6) Criar `LivroService`

Implementar regras de negócio:

- CRUD completo
- empréstimo com validação de conflito
- devolução com validação de estado

### 7) Criar `LivroController`

Mapeamento base: `/livros`.

Endpoints implementados:

- `GET /livros`
- `GET /livros/teste`
- `GET /livros/{id}`
- `POST /livros`
- `PUT /livros/{id}`
- `DELETE /livros/{id}`
- `PUT /livros/{id}/emprestar`
- `PUT /livros/{id}/devolver`

### 8) Popular banco com `data.sql`

Na inicialização, o sistema já carrega livros de exemplo no H2 para facilitar os testes.

### 9) Executar o projeto

#### Usando Maven Wrapper (recomendado)

Windows:
.\mvnw.cmd spring-boot:run

Linux/macOS:
./mvnw spring-boot:run

#### Ou usando Maven instalado

mvn spring-boot:run

Aplicação em:

- `http://localhost:8080`

### 10) Validar execução

- Endpoint teste: `http://localhost:8080/livros/teste`
- H2 Console: `http://localhost:8080/h2-console`

---

## 🧪 Dados iniciais no H2

O projeto carrega 3 livros automaticamente no startup.

Exemplo de consulta:

```http
GET http://localhost:8080/livros
```

---

## 🔍 Endpoints da API

| Método | Endpoint | Descrição |
|---|---|---|
| GET | `/livros` | Lista todos os livros |
| GET | `/livros/teste` | Verifica se API está ativa |
| GET | `/livros/{id}` | Busca livro por ID |
| POST | `/livros` | Cadastra novo livro |
| PUT | `/livros/{id}` | Atualiza dados do livro |
| DELETE | `/livros/{id}` | Remove livro |
| PUT | `/livros/{id}/emprestar` | Marca livro como emprestado |
| PUT | `/livros/{id}/devolver` | Marca livro como devolvido |

### Exemplo de body para criação/atualização

```json
{
  "id": 1,
  "titulo": "Java para Web",
  "autor": "Willian Santos",
  "emprestado": false,
  "dataEmprestimo": null
}
```

---

## 🧪 Testando no Postman/Insomnia

Sequência sugerida de validação:

1. `GET /livros/teste`
2. `GET /livros`
3. `POST /livros`
4. `GET /livros/{id}` do item criado
5. `PUT /livros/{id}`
6. `PUT /livros/{id}/emprestar`
7. `PUT /livros/{id}/devolver`
8. `DELETE /livros/{id}`

---

## 🖼️ Screenshots obrigatórias

Crie a pasta `docs/screenshots/` e salve as imagens conforme padrão:

- `01-estrutura-projeto.png`
- `02-app-rodando.png`
- `03-endpoint-teste.png`
- `04-lista-livros.png`
- `05-postman-criar-livro.png`
- `06-h2-console.png`

Guia detalhado de padrão visual em:

- [`docs/screenshots/GUIA-SCREENSHOTS.md`](docs/screenshots/GUIA-SCREENSHOTS.md)

---

## 🔗 Repositório

Clone o projeto:

git clone https://github.com/Willian-Santoss/biblioteca-api-main.git

---

## 🧯 Solução de problemas comuns

### Porta 8080 ocupada

Altere em `application.properties`:

```properties
server.port=8081
```

### Wrapper não executa no Windows

Use:

```bash
.\mvnw.cmd clean test
```

### Banco H2 não abre

Verifique:

- URL JDBC: `jdbc:h2:mem:biblioteca`
- User: `sa`
- Password: *(vazia)*

---

## 👤 Autor

**Willian Santos**

- GitHub: https://github.com/Willian-Santoss
- LinkedIn: https://linkedin.com/in/willian-santos-b848242bb

---

## 📄 Licença

Uso educacional.
