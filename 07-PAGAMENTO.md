# 07 — Pagamento

Sem cobrar, nao tem caixa rapido. Esse passo e o que diferencia um SaaS de um experimento.

---

## Decisao previa: Stripe ou Mercado Pago

| Criterio | Stripe | Mercado Pago |
|---|---|---|
| Cobranca recorrente | excelente | funcional |
| Pagamento via PIX | sim (mais lento de setup) | nativo, instantaneo |
| Cartao internacional | sim, simples | dificil |
| Documentacao | melhor do mercado | razoavel |
| Taxa | ~3.99% + R$ 0,39 | ~3.79% + variavel |

**Regra de bolso:** se 100% dos clientes sao Brasil + voce quer aceitar PIX, **Mercado Pago**. Se voce ja conhece Stripe ou tem cliente fora, **Stripe**.

A maioria dos casos do Caixa Rapido: **Stripe + PIX habilitado** funciona bem.

---

--- COMECO DO PROMPT ---

Voce e um senior engineer especializado em integracao de pagamentos. Sua missao: implementar cobranca recorrente no projeto, com checkout, webhook, e atualizacao do plano do usuario.

# Contexto

<arquitetura>
{COLE arquitetura.md}
</arquitetura>

<mvp>
{COLE mvp.md, parte do modelo de cobranca}
</mvp>

# Decisao

Vou usar: **{Stripe | Mercado Pago}**

Plano:
- Nome: {ex: "Pro"}
- Valor: R$ {X}/mes
- Trial: {0, 7 ou 14 dias}
- Moeda: BRL
- Meios de pagamento: {cartao + pix?}

# Tarefa

## 1. Antes de codificar
Me liste o que eu preciso configurar manualmente no painel do {Stripe/MP} ANTES de voce escrever qualquer codigo. Passos numerados, com link, sem encurtar:

- Criar conta
- Ativar pagamento em BRL
- Habilitar PIX (se aplicavel)
- Criar produto + preco
- Pegar `STRIPE_SECRET_KEY`, `STRIPE_PUBLISHABLE_KEY`, `STRIPE_WEBHOOK_SECRET`, `STRIPE_PRICE_ID`
- Configurar webhook (endpoint + eventos: `checkout.session.completed`, `customer.subscription.updated`, `customer.subscription.deleted`, `invoice.payment_failed`)

## 2. Codigo do checkout

`app/api/stripe/checkout/route.ts` — Server route que:
- Recebe `userId`
- Cria/recupera `stripe_customer_id` no banco
- Cria sessao de checkout com o `STRIPE_PRICE_ID` em modo `subscription`
- Retorna URL pra redirecionar o usuario

`components/CheckoutButton.tsx` — botao que chama essa rota e redireciona.

## 3. Webhook

`app/api/stripe/webhook/route.ts` que trata:
- `checkout.session.completed` — marca usuario como `plan = 'paid'`, salva `stripe_subscription_id`
- `customer.subscription.updated` — atualiza status (active, past_due, canceled)
- `customer.subscription.deleted` — marca como `plan = 'free'`
- `invoice.payment_failed` — marca status, manda email avisando

Importante:
- Use `verifyWebhookSignature` da SDK
- Idempotente (se receber 2x, nao quebra)
- Loga em `console.error` em caso de falha pra eu ver no Vercel

## 4. UI

- Pagina `/billing` na area logada: mostra plano atual, opcao de assinar (se free), opcao de gerenciar assinatura (se paid — link pro Customer Portal do Stripe)
- Paywall (do prompt 06) agora redireciona pro `/billing` ao inves de uma string generica

## 5. Como testar

Me ensine a testar localmente com `stripe listen` (ou equivalente do MP). Cartoes de teste, fluxo completo, como verificar no banco.

Antes de codificar, mostre o plano de arquivos. Depois que eu aprovar, codifique.

--- FIM DO PROMPT ---

---

## Checklist antes de lancar

- [ ] Cartao de teste passa o checkout e o `users.plan` muda pra `paid`
- [ ] Cancelamento via Customer Portal e refletido no banco
- [ ] Pagamento que falha (cartao recusado de teste) gera email e nao trava o app
- [ ] Webhook esta configurado em producao no painel do Stripe (nao so local)
- [ ] PIX testado em real com R$ 1 (vale a pena, da pra estornar)

## Erro mais comum

99% dos bugs em integracao de pagamento sao **webhook nao chegando**. Se o checkout funciona mas o `plan` nao muda, e o webhook. Verifique:

1. URL do webhook esta certa em producao
2. `STRIPE_WEBHOOK_SECRET` da producao (nao do local)
3. Logs do Vercel mostram que o request chegou
4. O codigo nao esta lendo `request.body` antes da verificacao de assinatura
