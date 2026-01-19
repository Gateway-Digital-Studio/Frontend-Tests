# Teste Técnico - Desenvolvedor React Native

## Objetivo

Desenvolver um aplicativo mobile de gestão de imóveis utilizando React Native com Expo, consumindo uma API GraphQL.

## API

**Endpoint:** `https://portly-drafty-pondskater.gigalixirapp.com/graphql`


### Schema GraphQL

#### Queries

```graphql
# Retorna o usuário autenticado
query Me {
  me {
    id
    name
    email
  }
}

# Lista todos os imóveis
query Enterprises($filter: EnterpriseFilter) {
  enterprises(filter: $filter) {
    id
    name
    listingType  # SALE ou RENT
    price
    gallery      # Array de URLs de imagens
    user {
      id
      name
    }
  }
}

# Busca um imóvel específico
query Enterprise($id: ID!) {
  enterprise(id: $id) {
    id
    name
    listingType
    price
    gallery
    user {
      id
      name
    }
  }
}
```

#### Mutations

```graphql
# Login - retorna token JWT
mutation SignIn($email: String!, $password: String!) {
  signIn(email: $email, password: $password) {
    token
    user {
      id
      name
      email
    }
  }
}

# Criar imóvel (requer autenticação)
mutation CreateEnterprise($input: EnterpriseInput!) {
  createEnterprise(input: $input) {
    id
    name
    listingType
    price
    gallery
  }
}

# Atualizar imóvel (requer autenticação + ser dono)
mutation UpdateEnterprise($id: ID!, $input: EnterpriseInput!) {
  updateEnterprise(id: $id, input: $input) {
    id
    name
    listingType
    price
    gallery
  }
}

# Deletar imóvel (requer autenticação + ser dono)
mutation DeleteEnterprise($id: ID!) {
  deleteEnterprise(id: $id) {
    id
  }
}
```

#### Input Types

```graphql
input EnterpriseInput {
  name: String
  listingType: ListingType  # SALE ou RENT
  price: Decimal
  gallery: [String]         # URLs das imagens
}

input EnterpriseFilter {
  listingType: ListingType
  minPrice: Decimal
  maxPrice: Decimal
}

enum ListingType {
  SALE
  RENT
}
```

### Autenticação

Após o login, inclua o token no header de todas as requisições autenticadas:

```
Authorization: Bearer <token>
```

---

## Funcionalidades Esperadas

### 1. Tela de Login
- Campos de email e senha
- Validação de campos
- Tratamento de erro de autenticação
- Redirecionamento após login bem-sucedido

### 2. Tela de Listagem (Meus Imóveis)
- Exibir imóveis do usuário logado
- Mostrar imagem principal, nome e preço
- Indicar se é venda ou aluguel
- Opção de editar e deletar cada imóvel
- Confirmação antes de deletar

### 3. Tela de Cadastro/Edição de Imóvel
- Campo: Título do anúncio (name)
- Seleção: Venda ou Aluguel (listingType)
- Campo: Valor (price)
- Galeria de imagens (gallery) - pode usar URLs mockadas
- Validação dos campos obrigatórios
- Feedback de sucesso/erro

### 4. Tela de Detalhes do Imóvel
- Exibir todas as informações
- Galeria de imagens com navegação
- Mostrar valor formatado em R$

---

## Requisitos Técnicos

### Obrigatórios

| Requisito | Descrição |
|-----------|-----------|
| Framework | React Native com Expo |
| Linguagem | JavaScript + TypeScript |
| GraphQL | Apollo Client, urql ou outra lib |
| Navegação | Expo Router ou React Navigation |
| Estados | Tratamento de loading e erros |

### Gerenciamento de Estado
- Livre escolha: estado local, Context API ou qualquer biblioteca
- Avaliaremos o uso consciente, não a ferramenta escolhida

---

## Diferenciais (não obrigatórios)

- Testes automatizados
- Persistência do token (AsyncStorage)

---

## Entrega

1. Subir o projeto em um repositório Git (GitHub, GitLab, etc)
2. Incluir um README com:
   - Como rodar o projeto
   - Decisões técnicas
   - O que faria diferente com mais tempo
3. Enviar o link do repositório para **psdev7@gmail.com**

**Prazo: 3 dias**

---

## Exemplo de Requisição

```bash
# Login
curl -X POST https://portly-drafty-pondskater.gigalixirapp.com/graphql \
  -H "Content-Type: application/json" \
  -d '{"query": "mutation { signIn(email: \"test@gateway.com\", password: \"test\") { token user { id name } } }"}'

# Listar imóveis (com token)
curl -X POST https://portly-drafty-pondskater.gigalixirapp.com/graphql \
  -H "Content-Type: application/json" \
  -H "Authorization: Bearer SEU_TOKEN_AQUI" \
  -d '{"query": "{ enterprises { id name listingType price gallery } }"}'
```

---

Boa sorte!
