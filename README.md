
# Encurtador de URLs

Esta aplicação tem como objetivo transformar URLs longas e complexas em links curtos e fáceis de compartilhar. 
Ideal para redes sociais, mensagens ou qualquer situação em que o espaço seja limitado, o encurtador de URLs oferece uma interface simples e intuitiva para gerar links curtos rapidamente. 
Além disso, a aplicação pode incluir funcionalidades adicionais como estatísticas de acesso, data de expiração dos links, redirecionamento personalizado e proteção por senha.


## Demonstração - TODO

TODO


## Screenshots - TODO

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## Variáveis de Ambiente - TODO

Para rodar esse projeto, você vai precisar adicionar as seguintes variáveis de ambiente no seu .env

`API_KEY`

`ANOTHER_API_KEY`


## Rodando localmente - TODO

Clone o projeto

```bash
  git clone https://github.com/danilo-righetto/url-shortener
```

Entre no diretório do projeto

```bash
  cd url-shortener
```

Instale as dependências - TODO

```bash
  npm install
```

Inicie o servidor - TODO

```bash
  npm run start
```


## Instalação - TODO

Instale my-project com npm

```bash
  npm install my-project
  cd my-project
```
    
## Deploy - TODO

Para fazer o deploy desse projeto rode

```bash
  npm run deploy
```


## Rodando os testes - TODO

Para rodar os testes, rode o seguinte comando

```bash
  npm run test
```


## Documentação

Desenvolver uma API backend para encurtamento de URLs, permitindo que os usuários enviem uma URL longa e recebam uma versão curta. 
A aplicação também deve redirecionar os acessos da URL curta para o destino original, armazenar estatísticas básicas e garantir escalabilidade, manutenibilidade e clareza de código.

### Arquitetura do Projeto

Dividida em camadas bem definidas para separar responsabilidades (exemplo com typescript):

```bash
src/
├── domain/             # Regras de negócio (Entidades, Interfaces, Use Cases)
├── application/        # Casos de uso (Application Services)
├── infrastructure/     # Comunicação externa (DB, Redis, Logger)
├── presentation/       # Controllers, rotas e validações
├── shared/             # Helpers, erros, configurações comuns
└── main.ts             # Ponto de entrada
```

### Padrão de Commits

Esse projeto utiliza o "[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)".
Utilize sempre o "[Conventional Commits](https://www.conventionalcommits.org/en/v1.0.0/)" em cada alteração do projeto!

### Fluxo de Funcionamento

1. Usuário envia uma URL longa via POST /shorten.
2. O sistema gera um hash único e armazena a correspondência no banco de dados.
3. O sistema retorna a URL encurtada (https://short.ly/abc123).
4. Quando alguém acessa /abc123, o sistema redireciona para a URL original.

### Requisitos Técnicos

> **Linguagem**: TypeScript (Node.js) ou PHP

> **Framework**: Express.js (com TypeScript) ou Laravel/Symfony

> **Banco de Dados**: PostgreSQL ou MongoDB

> **Cache**: Redis (para redirecionamento rápido)

> **Outros**: Docker, Swagger/OpenAPI, ESLint/Prettier, PHPUnit

### Design de Classes e Responsabilidades (Princípios SOLID)

#### S - Single Responsibility Principle

Cada classe tem uma responsabilidade única:

- `UrlShortenerService` → lógica de encurtamento
- `UrlRepository` → acesso ao banco
- `RedirectController` → apenas para redirecionar

#### O - Open/Closed Principle

A lógica de geração de hash pode ser trocada sem alterar o serviço:

```ts
interface HashGenerator {
  generate(url: string): string;
}
```

#### L - Liskov Substitution Principle

Qualquer implementação de `HashGenerator` deve poder ser usada no lugar de outra sem quebrar o sistema.

#### I - Interface Segregation Principle

Evita interfaces muito grandes, dividindo responsabilidades:

```ts
interface UrlReader {
  findByHash(hash: string): Url | null;
}

interface UrlWriter {
  save(url: Url): void;
}
```

#### D - Dependency Inversion Principle

As dependências (como repositórios) são injetadas por abstrações:

```ts
class UrlShortenerService {
  constructor(private readonly repo: UrlRepository) {}
}
```

### Segurança

- Validação de URLs maliciosas
- Limitação de taxa (`rate limiting`)
- Códigos curtos com tempo de expiração (opcional)
- Sanitização de entradas

### Possíveis Extensões Futuras

- Dashboard com visualização das URLs encurtadas
- Autenticação para usuários criarem e gerenciarem suas URLs
- Personalização de aliases (`/meu-link`)
- QR Code automático


## Autores

- [@danilorighetto](https://www.linkedin.com/in/danilo-righetto/)


## Referência

 - [Instagram - Fernanda kipper.dev](https://www.instagram.com/kipper.dev/)
 - [Ideias de Projetos BACKEND AVANÇADOS pra TE DESTACAR](https://www.youtube.com/watch?v=AD0FbOR4Zj8)


## Licença

[MIT](https://choosealicense.com/licenses/mit/)

