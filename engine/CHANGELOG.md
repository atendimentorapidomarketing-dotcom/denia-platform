# Changelog — DENIA Engine

## 30.0.0 — 2026-10-07

Substitui o Worker v29.x por um motor reescrito em torno de uma máquina de estados durável.
Compatível com as tabelas existentes do D1 (histórico preservado).

### Corrigido
- Perda de contexto e reabertura de casos: estado do caso (`d30_casos`) com etapas e fatos;
  importação automática de casos antigos; caso AGENDADO nunca volta para coleta.
- Perguntas repetidas: guarda determinística bloqueia perguntar de novo serviço, bairro,
  endereço e nome registrados; "ok/obrigado" sem pergunta pendente não geram resposta.
- Promessas sem ação: "enviamos/consultamos/agendado/confirmado/cancelado" só depois de a ação
  ter acontecido (message id da Meta).
- Envios sem mensagem nova: nada é enviado por cron, exceto consultas aceitas à noite e
  enviadas às 8h (até 16 h depois); mensagens atrasadas mais de 15 min não são respondidas.
- Prestador tratado como cliente: lista oficial por telefone (inclusive wa_id sem o nono dígito)
  tem precedência; técnicos do D1 também nunca entram no fluxo de cliente.
- Prestador errado / nomes duplicados: roteamento por telefone + área, palavras-chave
  determinísticas antes da sugestão da IA.
- Mistura de casos: consulta por caso (`d30_consultas`) com "Caso #N"; vínculo pela mensagem
  citada (context.id); pergunta qual caso quando houver mais de um.
- Valor inventado / markup: valor só conta se o prestador escreveu o número; pergunta se é
  final ou só a parte dele; acréscimo configurável (`MARKUP_PERCENT`).
- Confirmação indevida: AGENDADO só com confirmação do prestador depois do aceite do cliente.
- Cancelamento: nunca automático; vira alerta para a equipe.
- Cobertura de região, bairro como requisito de orçamento, bairro em serviço de balcão, CPF e
  telefones: frases bloqueadas antes do envio.
- Cota do D1: consultas indexadas, sem varreduras no cron, sem migrações repetidas; KV grava
  só quando a etapa muda.
- Treinamento: versionado, edição parcial, restauração, nunca esvazia campo sem confirmação.
- Segurança: painéis com senha (`PAINEL_SENHA`), verificação da assinatura da Meta
  (`META_APP_SECRET`), rota pública de envio removida, conversão automática de "Mirella" removida.

### Removido
- Comandos da equipe por WhatsApp (camadas v10–v15).
- Ponte KV por prestador (v29.1–v29.6) e fluxo de pendências legado.

### Rollback
Cloudflare → Worker → Deployments → versão anterior → Rollback. As tabelas `d30_` não interferem na v29.
