# DENIA Platform V3 — Cloudflare Ready

Primeira versão publicável da plataforma DENIA.

## O que mudou
- Next.js App Router rodando via **vinext**
- Build via **Vite**
- Deploy via **Cloudflare Workers**
- `vite.config.ts` configurado
- `worker/index.ts` configurado
- `wrangler.jsonc` configurado
- primeira publicação não depende de D1 nem de secrets
- Clerk fica opcional até configurarmos as chaves
- Home futurista da V2 preservada

## Cloudflare — campos exatos

**Build command**
```bash
npm run build
```

**Deploy command**
```bash
npx wrangler deploy
```

**Root directory**
```text
/
```

A integração Vite da Cloudflare gera a configuração de saída durante `vite build`; depois `wrangler deploy` usa esse build.

## Depois que a Home estiver no ar
1. configurar Clerk
2. criar Organization da operação principal
3. criar D1 `denia-saas`
4. ligar DENIA Control ao DENIA Engine
5. painel Meta + OpenAI
6. Embedded Signup / WhatsApp Coexistence
