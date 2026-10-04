
# DENIA Platform V2

Base inicial da plataforma SaaS DENIA com **Home futurista**, autenticação, dashboard e início da integração WhatsApp por Coexistência.

## O que já veio nesta versão
- Home pública mais premium e interativa
- Login e cadastro com Clerk
- Dashboard inicial
- Páginas: Conversas, Treinar IA, WhatsApp, API, Configurações
- Estrutura multiempresa
- Esqueleto de conexão do WhatsApp por Coexistência
- Schema D1
- Pronto para Cloudflare via vinext

## Ações agora

### 1) GitHub
Crie um repositório privado, por exemplo:
`denia-platform`

### 2) Suba o projeto
Extraia este ZIP e envie tudo para o repositório.

### 3) Instale e rode localmente
```bash
npm install
npm run dev
```

### 4) Configure o Clerk
```bash
npx -y clerk@latest init
npx -y clerk@latest enable orgs
```

### 5) Configure o Cloudflare D1
```bash
npx wrangler login
npx wrangler d1 create denia-saas
npx wrangler d1 execute denia-saas --remote --file=./sql/schema.sql
```
Depois coloque o `database_id` em `wrangler.jsonc`.

### 6) Configure variáveis de ambiente
Preencha `.env.example` com seus valores reais.

### 7) Deploy
Conecte o repositório ao Cloudflare Workers/Pages ou use:
```bash
npm run cf:build
npm run deploy
```

## Próxima entrega técnica
1. Fazer login/cadastro reais
2. Criar Organization "sua operação"
3. Publicar a Home
4. Ligar Dashboard ao DENIA Engine
5. Mostrar OpenAI/Meta usage no painel
6. Completar Coexistência da Meta
