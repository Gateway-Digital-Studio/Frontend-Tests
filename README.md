# Teste Técnico — Desenvolvedor(a) React Native (Expo)

---

## Objetivo

Desenvolver um pequeno aplicativo mobile de **blog** utilizando React Native com Expo, consumindo uma API GraphQL pública.

> O foco do teste é avaliar **organização de código**, **componentização**, **consumo de GraphQL** e **clareza na solução** — não complexidade excessiva.

---

## API

Utilize a API **GraphQL Zero**:

```
https://graphqlzero.almansi.me/api
```

Documentação: https://graphqlzero.almansi.me/

### Recursos disponíveis

| Recurso    | Campos principais        |
|------------|--------------------------|
| `posts`    | id, title, body, user    |
| `users`    | id, name, email          |
| `comments` | id, body, post           |

---

## Funcionalidades Obrigatórias

### 1. Lista de Posts

- Buscar posts via GraphQL
- Exibir lista contendo:
  - Título
  - Preview do conteúdo
  - Nome do autor
- Cada item deve ser um **componente reutilizável**
- Ao clicar em um post, navegar para a tela de detalhe

### 2. Detalhe do Post

- Buscar o post por ID via GraphQL
- Exibir:
  - Título completo
  - Conteúdo completo
  - Informações do autor
  - **Listar os comentários do post**
- Botão para voltar à lista

> Os comentários devem ser obtidos a partir da própria API GraphQL.

### 3. Criar Post

- Formulário com:
  - Título
  - Conteúdo
- Enviar os dados utilizando **mutation GraphQL** (fake — não persiste)
- Após salvar, voltar para a lista

---

## Requisitos Técnicos

### Obrigatórios

| Requisito | Descrição |
|-----------|-----------|
| **Framework** | React Native com Expo |
| **Linguagem** | JavaScript + TypeScript |
| **GraphQL** | Apollo Client, urql ou outra lib de sua preferência |
| **Navegação** | Expo Router ou React Navigation |
| **Estados** | Tratamento de loading e erros |

### Gerenciamento de Estado

- **Livre**: pode usar estado local, Context API ou qualquer biblioteca
- Avaliaremos uso consciente, não a ferramenta escolhida

### Design

- **Livre**
- Avaliamos:
  - Clareza
  - Consistência
  - Usabilidade básica

## Diferenciais (não obrigatórios)

- [ ] Pull-to-refresh na lista
- [ ] Paginação
- [ ] Custom hooks para dados
- [ ] README explicando decisões técnicas

---

## O que NÃO é necessário

- ~~Testes automatizados~~
- ~~Editar ou deletar posts~~
- ~~Design avançado~~

---

## Entrega

1. Subir o projeto em um **repositório Git** (GitHub, GitLab, etc)
2. Incluir um **README** com:
   - Como rodar o projeto
   - Decisões técnicas
   - O que faria diferente com mais tempo
3. Enviar o link do repositório para o email [psdev7@gmail.com]

---

## Prazo

**5 dias** a partir do recebimento do teste.

---

## Considerações Finais

> O foco do teste é **qualidade de código** e **clareza da solução**.
> Não buscamos soluções complexas, mas sim soluções **bem feitas**.

**Boa sorte!**
