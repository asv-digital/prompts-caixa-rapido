# 04 — Arquitetura

Escolher stack, definir estrutura, ja deixar tudo pronto pra Claude Code construir no proximo passo.

---

--- COMECO DO PROMPT ---

Voce e um arquiteto de software senior. Sua missao: definir a arquitetura mais simples possivel para construir o MVP do meu SaaS em ate 14 dias.

# Contexto

Cole o conteudo do `mvp.md` (do prompt 03):

<mvp>
{COLE AQUI}
</mvp>

# Stack default que eu prefiro (mude SO se houver razao tecnica forte)

- **Frontend + Backend:** Next.js 15 (App Router) + TypeScript
- **Hospedagem:** Vercel
- **Banco:** Supabase (Postgres + Auth + Storage)
- **Pagamento:** Stripe (cobranca recorrente em BRL)
- **Email transacional:** Resend
- **IA (se precisar):** Claude API
- **CSS:** Tailwind + shadcn/ui

# O que voce entrega

## 1. Validacao da stack

Olhando o `mvp.md`, essa stack atende? Se nao, qual a alteracao **minima** necessaria? Justifique. Nao troque por gosto, troque so se for necessario.

## 2. Modelo de dados

Liste as tabelas necessarias com colunas. Formato:

```
### users (Supabase Auth ja gerencia, voce so estende)
- id (uuid)
- email
- created_at
- plan (free | paid)
- stripe_customer_id

### {tabela_principal_do_dominio}
- id
- user_id (fk)
- ...

### subscriptions (cache do Stripe)
- ...
```

Inclua so o necessario pro MVP. Sem tabela "para o futuro".

## 3. Estrutura de pastas

```
meu-saas/
├── app/
│   ├── (marketing)/      # landing
│   ├── (app)/            # area logada
│   ├── api/
│   │   ├── stripe/webhook/
│   │   └── ...
├── components/
├── lib/
│   ├── supabase/
│   ├── stripe/
│   └── ...
├── .env.example
└── ...
```

Adapte pra esse projeto.

## 4. Variaveis de ambiente

Lista de TODAS as `.env` que vou precisar:

```
NEXT_PUBLIC_SUPABASE_URL=
NEXT_PUBLIC_SUPABASE_ANON_KEY=
SUPABASE_SERVICE_ROLE_KEY=
STRIPE_SECRET_KEY=
STRIPE_WEBHOOK_SECRET=
NEXT_PUBLIC_STRIPE_PRICE_ID=
RESEND_API_KEY=
ANTHROPIC_API_KEY=  # se usar IA
```

## 5. Riscos tecnicos

3-5 coisas que costumam dar problema com essa stack neste tipo de projeto. Para cada uma, qual a precaucao.

## 6. Ordem de construcao

Liste em ate 12 etapas a ordem de construir, do zero ao deploy:

```
1. Criar projeto Next.js + Tailwind + shadcn
2. Configurar Supabase (criar tabelas)
3. Auth (signup/login/logout)
4. Layout da area logada
5. Feature core (a do MVP)
6. Stripe checkout
7. Webhook do Stripe (atualizar plan no banco)
8. Bloqueio de feature pra plano free
9. Email de boas-vindas (Resend)
10. Landing page
11. Deploy Vercel + dominios
12. Smoke test fim a fim
```

## 7. Definicao de pronto

Frase de 1-2 linhas: "O MVP esta pronto quando..." (deixe especifico, mensuravel)

Comece a montar.

--- FIM DO PROMPT ---

---

## Saida esperada

`meu-saas/arquitetura.md` com a stack, modelo de dados, estrutura de pastas e ordem de construcao. Esse arquivo voce vai colar no Claude Code no proximo prompt.
