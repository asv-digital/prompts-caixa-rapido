# 09 — Feedback

Os primeiros 10 clientes sao seu mapa do tesouro. Esse passo monta o sistema pra extrair o maximo deles.

---

--- COMECO DO PROMPT ---

Voce e um especialista em customer success para SaaS B2B. Sua missao: montar um sistema simples de feedback continuo dos primeiros 10-30 clientes do meu SaaS.

# Contexto

<nicho>
{COLE NICHO.MD}
</nicho>

<mvp>
{COLE MVP.MD}
</mvp>

Numero atual de clientes pagantes: {N}

# Restricao

- Eu nao tenho equipe — eu mesmo vou conversar com clientes
- Maximo 5h/semana pra customer success
- Quero conversa real, nao formulario NPS frio
- Quero descobrir: o que mantem cliente / o que faz cliente cancelar / qual a proxima feature de maior impacto

# O que voce me entrega

## 1. Cadencia de contato

Tabela com momentos chave de contato:

| Momento | Tipo | Canal | O que perguntar |
|---------|------|-------|-----------------|

Sugestao de momentos minimos:
- Dia 0 (cadastro): mensagem de boas-vindas + pergunta unica
- Dia 3: chegou em algum lugar? travou em algo?
- Dia 14: feedback do que esta usando + nao esta usando
- Dia 30: pergunta-mae (se cancelasse hoje, por que?)
- Quando solta uma feature: pediu? testou? gostou?
- Quando cancela: por que? (mas SEM tentar reverter forcadamente)

## 2. Mensagens prontas

Cada uma das mensagens da tabela acima, escrita pronta pra colar. Curta, sem clichê, sem "esperamos que esteja tendo uma otima experiencia".

## 3. A pergunta-mae (Sean Ellis test)

> "Como voce se sentiria se nao pudesse mais usar {produto}?"
> a) Muito decepcionado
> b) Um pouco decepcionado
> c) Indiferente

Se 40%+ respondem "muito decepcionado", voce tem product-market fit. Roteiro pra fazer essa pergunta de forma natural no dia 30.

## 4. Sistema de organizacao

Como armazenar o feedback de forma que vire decisao. Sugiro estrutura simples em arquivo `feedback.md`:

```markdown
## {DATA} — {CLIENTE}
**Canal:** whatsapp / call / email
**Estagio:** dia 3 / dia 14 / dia 30 / outro
**Resumo:** 2-3 linhas
**Tags:** #feature-X #bug #onboarding #preco
**Acao gerada:** {ou "nenhuma"}
```

E um `feedback-resumo.md` que voce atualiza toda sexta com:
- Top 3 dores recorrentes
- Top 3 elogios recorrentes
- Top 3 features pedidas
- Casos de churn (motivo + cliente + data)
- Decisoes da semana

## 5. Como decidir o que construir a seguir

Regrinha simples e dura:

> So entra na proxima sprint o que apareceu em **3+ conversas independentes** OU o que esta gerando **churn**.

Tudo o resto: anota e congela. A gente nao constroi pelo loud user. Constroi pelo padrao.

## 6. Sinais de churn antecipado

5-7 sinais que voce pode rastrear no banco/log que indicam que o cliente provavelmente vai cancelar nos proximos 30 dias. Ex: nao logou ha X dias, nao usou a feature core ha Y dias, etc. Para cada sinal, qual a acao de retencao (mensagem, ligacao, oferta).

Comece a montar.

--- FIM DO PROMPT ---

---

## Saida esperada

`meu-saas/customer-success.md` com cadencia, mensagens e sistema. Em 30 dias rodando isso, voce sabe se o produto vai ou se precisa pivotar.

## Aviso

A coisa mais cara em SaaS e construir feature errada. A segunda mais cara e nao construir feature certa porque nao escutou o cliente. Esse passo previne as duas.
