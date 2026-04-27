# 00 — Leia primeiro

Esse pacote e simples: **pegar uma dor especifica de um nicho que paga, resolver com SaaS pequeno, cobrar mensalidade.**

Nao e teoria. Nao e visao de longo prazo. E *caixa rapido*. O nome e literal.

## A regra das 3 perguntas

Antes de comecar qualquer SaaS, voce tem que conseguir responder:

1. **Quem paga?** — Nome, cargo, empresa, ou perfil de pessoa especifica. Nao "PMEs". Nao "gestores". Nome com cara.
2. **Quanto paga?** — Quanto essa pessoa ja gasta hoje pra resolver essa dor (em ferramenta, mao de obra, tempo)?
3. **Como vou achar mais delas?** — Existe canal pra encontrar 100 dessas pessoas em ate 30 dias? (LinkedIn, grupo de Whatsapp, evento, lista, indicacao)

Se voce nao consegue responder as tres, **nao comece**. Volta pro Prompt 01 e refina.

## A ordem importa

A ordem dos prompts nao e estetica. E logica de negocio:

```
NICHO -> VALIDACAO -> MVP -> ARQUITETURA -> LANDING -> BUILD -> PAGAMENTO -> LANCAMENTO -> FEEDBACK -> ESCALA
```

Cada etapa pressupoe que a anterior deu sinal verde. Se a `VALIDACAO` nao validou, **nao construa o MVP**. Volte e ache outro nicho.

## O que voce NAO vai encontrar aqui

- "Como ficar rico em 30 dias"
- Lista de "ideias quentes de SaaS"
- Promessa de SaaS que se mantem sozinho

O que voce vai encontrar e: estrutura honesta + prompts que funcionam.

## Stack que vamos usar

Pra deixar simples e barato:

- **Frontend + Backend:** Next.js + Vercel (gratis ate dar trafego)
- **Banco:** Supabase (gratis ate ~50k linhas)
- **Auth:** Supabase Auth ou Clerk
- **Pagamento:** Stripe (Brasil) ou Mercado Pago
- **Email transacional:** Resend (gratis ate 3k/mes)
- **IA:** Claude API (paga por uso, sem mensalidade)

Custo total mensal antes do primeiro cliente: **R$ 0 a R$ 50**.

## Mentalidade

- Voce nao esta criando "o" SaaS. Esta criando "um" SaaS. O proximo voce faz mais rapido.
- 80% feito enviado >> 100% feito guardado
- Cliente paga para resolver dor, nao para usar tecnologia
- Cobre desde o dia 1. Gratis nao valida nada, so atrai curiosos

Vai pro `01-NICHO.md`.
