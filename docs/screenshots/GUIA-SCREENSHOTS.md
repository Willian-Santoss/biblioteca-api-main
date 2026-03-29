# Mini-guia de screenshots (padrão do projeto Biblioteca API)

Este guia padroniza as imagens usadas no `README.md` para manter um visual limpo, técnico e profissional.

## 1) Nomes de arquivo (obrigatório)

Use exatamente estes nomes:

- `01-estrutura-projeto.png`
- `02-app-rodando.png`
- `03-endpoint-teste.png`
- `04-lista-livros.png`
- `05-postman-criar-livro.png`
- `06-h2-console.png`

## 2) Conteúdo de cada imagem

### `01-estrutura-projeto.png`
- VS Code aberto
- Explorer visível com os pacotes `controller`, `service`, `repository`, `model`
- Arquivo `README.md` ou `LivroController.java` aberto

### `02-app-rodando.png`
- Terminal do VS Code mostrando aplicação em execução
- Evidência do startup do Spring Boot na porta `8080`

### `03-endpoint-teste.png`
- Navegador com `http://localhost:8080/livros/teste`
- Resposta: `API funcionando corretamente`

### `04-lista-livros.png`
- Navegador ou cliente HTTP com `GET /livros`
- Lista JSON dos livros retornada

### `05-postman-criar-livro.png`
- Requisição `POST /livros` no Postman/Insomnia/Thunder Client
- Body JSON visível + resposta `201 Created`

### `06-h2-console.png`
- Acesso ao `http://localhost:8080/h2-console`
- Login com JDBC URL e resultado de consulta na tabela `LIVROS`

## 3) Padrão visual recomendado

- **Formato:** PNG
- **Resolução sugerida:** 1366x768 ou 1920x1080
- **Tema do VS Code:** manter o mesmo em todas as capturas
- **Zoom:** 100% (evitar letras muito pequenas)
- **Corte:** remover áreas irrelevantes da tela

## 4) Boas práticas

- Evite dados pessoais visíveis (email, usuário, notificações)
- Feche abas desnecessárias
- Garanta nitidez e legibilidade
- Não misture formatos (`.png` e `.jpg`) nos arquivos obrigatórios

## 5) Checklist rápido antes do commit

- [ ] As imagens estão em `docs/screenshots/`
- [ ] Os nomes dos arquivos seguem o padrão
- [ ] O conteúdo das imagens corresponde ao que o README descreve
- [ ] As capturas estão legíveis e sem dados sensíveis

