
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


## Rodando localmente

Clone o projeto

```bash
  git clone https://github.com/danilo-righetto/url-shortener
```

Entre no diretório do projeto

```bash
  cd url-shortener/url
```

Instale as dependências

```bash
  npm install
```

Inicie o servidor

```bash
  npm run start
```

## Configuração do Ambiente

Configurações e dependências do projeto.

### Principais Dependências

```sh
pnpm add @nestjs/core @nestjs/common @nestjs/platform-express
pnpm add @nestjs/typeorm typeorm pg
pnpm add class-validator class-transformer
pnpm add shortid
pnpm add @nestjs/swagger swagger-ui-express
```

### Dependências de Desenvolvimento

```sh
pnpm add -D @nestjs/cli typescript ts-node nodemon jest @types/jest ts-jest
```

## Implementação dos Módulos

**UrlModule**

- POST /url → cria nova URL curta.
- GET /:shortId → redireciona para a URL original.
- GET /url/:id → retorna dados da URL.

**Exemplo de Entidade:**

```ts
@Entity()
export class Url {
  @PrimaryGeneratedColumn('uuid')
  id: string;

  @Column()
  originalUrl: string;

  @Column({ unique: true })
  shortCode: string;

  @Column({ default: 0 })
  visitCount: number;

  @CreateDateColumn()
  createdAt: Date;
}
```

## Rodando com Docker - TODO

Instale url-shortener com npm

```bash
  npm install url-shortener
  cd url-shortener
```
    
## Deploy - TODO

Para fazer o deploy desse projeto rode

```bash
  npm run deploy
```


## Rodando os testes

Para rodar os testes, rode o seguinte comando

```bash
  npm run test
```

### Cobertura de testes

```bash
pnpm test --coverage
```

## Middleware e Interceptores

**Middleware de Redirecionamento**

- Intercepta rota `/:shortCode`.

- Busca a URL original e redireciona com `response.redirect()`.

- Registra o evento no `AnalyticsService`.

**Interceptores**

- LoggingInterceptor → logs de requisições.

- TimeoutInterceptor → limita tempo de resposta.

- TransformInterceptor → padroniza respostas JSON.

## Módulo Analytics

- Captura logs de acesso via **Middleware**.

- Endpoint `/analytics/:id` retorna estatísticas de cliques, origem e data.

## Segurança e Boas Práticas

- Sanitizar entrada de URLs.

- Usar `helmet` e `rate-limiter` contra abuso.

- Validar origem das requisições.

- Hash opcional para URLs privadas.

- Logs estruturados com **Winston** ou **Pino**.

## Evolução e Escalabilidade

**Possíveis Extensões:**

- Painel web (Next.js / Vue.js) para gerenciar URLs.

- Suporte a expiração de links.

- API pública com chaves de acesso.

- Shortcodes personalizados.

- Integração com Redis para cache.

- Versionamento de API (v1, v2).

- Microserviço dedicado a redirecionamentos.

## Documentação

Desenvolver uma API backend para encurtamento de URLs, permitindo que os usuários enviem uma URL longa e recebam uma versão curta. 
A aplicação também deve redirecionar os acessos da URL curta para o destino original, armazenar estatísticas básicas e garantir escalabilidade, manutenibilidade e clareza de código.

Para mais informações sobre [Arquitetura do Projeto](./DOCS.md) pode ser encontrada [aqui](./DOCS.md).

### Swagger

Usar **@nestjs/swagger**:

```ts
const config = new DocumentBuilder()
  .setTitle('URL Shortener API')
  .setDescription('API para encurtar e gerenciar URLs')
  .setVersion('1.0.0')
  .build();
```


## Autores

- [@danilorighetto](https://www.linkedin.com/in/danilo-righetto/)


## Referência

 - [Instagram - Fernanda kipper.dev](https://www.instagram.com/kipper.dev/)
 - [Ideias de Projetos BACKEND AVANÇADOS pra TE DESTACAR](https://www.youtube.com/watch?v=AD0FbOR4Zj8)


## Licença

[MIT](https://choosealicense.com/licenses/mit/)

