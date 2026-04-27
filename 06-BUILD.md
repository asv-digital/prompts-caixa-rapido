# 06 — Build do MVP

Construir o produto com Claude Code, etapa por etapa, sem se perder.

---

## Antes de comecar

Voce ja tem `meu-saas/arquitetura.md` (do prompt 04) e a landing (do prompt 05). Agora vamos construir.

**Importante:** este prompt nao e UM prompt grande. Sao 3 mini-prompts que voce roda em sequencia, cada um pra uma fase do build.

---

## PROMPT A — Setup do projeto

--- COMECO DO PROMPT A ---

Voce e um senior fullstack engineer trabalhando comigo no Claude Code. Vamos iniciar o projeto. Sua missao agora: setup limpo, sem firula.

# Contexto da arquitetura

<arquitetura>
{COLE arquitetura.md DO PROMPT 04}
</arquitetura>

# Tarefa

1. Crie a estrutura inicial do Next.js 15 com TypeScript, Tailwind, shadcn/ui
2. Configure ESLint + Prettier basico
3. Crie `.env.example` com TODAS as variaveis listadas na arquitetura
4. Crie `lib/supabase/client.ts` e `lib/supabase/server.ts`
5. Crie `lib/stripe/client.ts`
6. Crie pasta `app/(marketing)` e `app/(app)` vazias
7. Configure middleware do Supabase Auth (so o esqueleto)
8. Crie `README.md` com:
   - Como rodar local
   - Como criar o projeto Supabase e popular tabelas (com SQL pronto)
   - Como criar produto/preco no Stripe
   - Como configurar webhook do Stripe local com `stripe listen`

NAO escreva ainda a feature core nem auth completo. So o esqueleto.

No final, me diga exatamente o que eu preciso fazer manualmente (criar conta Supabase, conta Stripe, etc.) com link e passos numerados.

--- FIM DO PROMPT A ---

---

## PROMPT B — Auth + feature core

Rode depois que o setup estiver pronto e voce ja configurou Supabase e Stripe.

--- COMECO DO PROMPT B ---

Continuando o projeto. Agora vamos implementar:

1. Auth completo (signup, login, logout, recuperar senha)
2. A feature core do produto
3. Bloqueio de feature pra usuario sem assinatura paga

# Contexto

<arquitetura>
{COLE arquitetura.md}
</arquitetura>

<mvp>
{COLE mvp.md}
</mvp>

# Tarefa

## Auth
- Use Supabase Auth, magic link OU email+senha (escolha o mais simples para o caso e justifique)
- Pagina `/login` e `/signup` com shadcn forms
- Apos login, redireciona pra `/app`
- Middleware protege `/app/*` pra nao logado

## Feature core
Implemente o fluxo descrito em `mvp.md` passo a passo. Crie:
- Rotas necessarias em `app/(app)/`
- Server Actions ou API routes pra cada operacao
- Componentes de UI (use shadcn quando possivel)
- Validacao com Zod
- Tratamento de erro com toast (sonner)

## Bloqueio de plano
- Cria `lib/auth/checkPlan.ts` que retorna `'free' | 'paid'`
- A feature core fica bloqueada pra `'free'` (mostra paywall)
- O paywall e simples: "Assine pra usar essa feature" + botao que vai pro checkout do Stripe

NAO implemente o checkout em si ainda — esse e o proximo prompt. So bloqueia.

Antes de codificar, me mostre o plano de arquivos que vai criar/editar (so a lista). Depois que eu aprovar, codifique.

--- FIM DO PROMPT B ---

---

## PROMPT C — Pagamento (Stripe)

Esta no proximo arquivo `07-PAGAMENTO.md`. Nao adianta o produto se voce nao consegue cobrar.

---

## Como nao se perder durante o build

1. **Faca commit a cada etapa que funciona.** Mesmo que pequeno. `git commit -m "auth funcionando"`. Cria pontos de retorno.
2. **Rode local depois de cada feature.** Nao codifique 3 features e teste tudo junto — vai dar problema e voce nao vai saber qual quebrou.
3. **Quando o Claude Code propor algo grande, peca pra dividir.** "Faca em etapas, espera minha confirmacao entre elas."
4. **Use `git diff` antes de aceitar mudanca.** Especialmente em `package.json`, `middleware.ts` e arquivos de config.

## Sinal de que voce ta bem

Apos PROMPT A: `npm run dev` roda sem erro, abre em `localhost:3000` e mostra hello world.
Apos PROMPT B: voce consegue se cadastrar, logar, ver a area logada, mas a feature core mostra paywall.
Apos PROMPT C (proximo): voce consegue pagar com cartao de teste e a feature core libera.

## Sinal de que voce ta mal

- Mais de 3 horas no mesmo erro: pare, leia atentamente a mensagem, considere reverter o ultimo passo
- "Funciona, mas eu nao sei por que": pare e peca pro Claude explicar antes de seguir
- Mudanca enorme em arquivo que voce nao pediu: rejeite, pergunte por que, peca menor
