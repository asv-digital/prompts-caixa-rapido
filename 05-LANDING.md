# 05 — Landing page

Criar a landing que converte antes do produto existir. Pode (e deve) usar pra rodar pre-vendas em paralelo com o build.

---

--- COMECO DO PROMPT ---

Voce e um copywriter direto + designer de landing pages B2B. Sua missao: gerar uma landing page completa, pronta para deploy no Vercel, que converta visitante interessado em "lead que paga" (ou pelo menos lead quente).

# Contexto

Cole abaixo:

<nicho>
{COLE NICHO.MD}
</nicho>

<mvp>
{COLE MVP.MD}
</mvp>

# Decisoes minhas

- Dominio: {meudominio.com.br ou ainda nao definido}
- Estagio: {pre-MVP / MVP em construcao / MVP pronto}
- CTA principal: {agendar conversa de 15min / pagar agora / entrar pra lista de espera}
- Preco que vou exibir: {R$ X/mes ou "sob consulta"}

# O que voce me entrega

## 1. Estrutura da landing

Liste as secoes em ordem, cada uma com:
- Titulo da secao
- Que pergunta da cabeca do visitante essa secao responde
- Decisao de design (texto / texto + imagem / video / depoimento / FAQ / etc.)

Estrutura basica que costuma converter (adapte ao caso):

```
1. Hero — promessa nuclear + CTA primario
2. Dor — o problema do cliente (sem mencionar voce)
3. Solucao — como o produto resolve em 3 passos
4. Demonstracao — print, video curto, ou print animado
5. Para quem e (e para quem nao e)
6. Preco — claro, sem trocadilho
7. Prova social — depoimentos, logos, numeros (ou "estamos comecando" honesto)
8. FAQ — 6-10 perguntas reais
9. CTA final
10. Rodape minimo
```

## 2. Copy completa

Para CADA secao, escreva o texto pronto pra colar:

- **Hero (titulo):** maximo 8 palavras, fala do beneficio especifico, sem clichê
- **Hero (subtitulo):** 1-2 linhas, fala pra QUEM e o QUE entrega
- **Hero (CTA):** verbo no infinitivo + beneficio. "Comecar agora" e ruim. "Calcular meu primeiro IRPF agora" e bom.
- **Dor:** lista de 3-5 sintomas que o cliente reconhece
- **Solucao:** 3 passos numerados, beneficio em cada um
- **Para quem e:** bullets de 3-5 itens
- **Para quem NAO e:** bullets de 2-3 itens (filtra publico errado)
- **FAQ:** 6-10 perguntas reais que voce ouviu na fase de validacao + respostas curtas

Regras de copy:
- Numero especifico vence adjetivo
- Use a linguagem do nicho, nao a sua
- Nao use "transforme", "revolucione", "descubra agora"
- Sem emoji, salvo se o publico for jovem

## 3. Implementacao tecnica

Me entregue o **codigo Next.js + Tailwind + shadcn/ui** da landing inteira, em arquivos reais:

```
app/
└── (marketing)/
    ├── page.tsx           # landing
    └── components/
        ├── Hero.tsx
        ├── Dor.tsx
        ├── Solucao.tsx
        ├── ParaQuem.tsx
        ├── Preco.tsx
        ├── Faq.tsx
        └── Cta.tsx
```

- Mobile-first
- Sem animacao excessiva (1 fade-in suave no hero, mais nada)
- Imagem placeholder com sugestao de o que colocar
- Botao de CTA usando shadcn `<Button>` com data-attribute `data-cta="hero"` para tracking

## 4. SEO basico

- `<title>` e `<meta description>` para a pagina
- Open Graph (titulo + descricao + imagem 1200x630 — sugira o conteudo)

## 5. Tracking

Como rastrear conversao sem ferramenta paga:
- Plausible (US$ 9/mes) ou Umami (gratis self-host) ou Vercel Analytics (gratis ate 2.5k events/mes)
- Eventos minimos: pageview, click_cta_hero, click_cta_final, submit_lead

Indique qual escolher e cole o snippet.

Comece pela secao 1.

--- FIM DO PROMPT ---

---

## Saida esperada

A landing inteira, codada, pronta pra colar no projeto Next.js que voce ja iniciou no prompt 04.

## Atalho

Voce pode publicar essa landing **antes** de ter o produto. Use ela pra rodar pre-vendas / lista de espera enquanto constroi o MVP. Se nenhuma pessoa se cadastrar em 7 dias com algum trafego, voce tem informacao valiosa: o nicho/produto precisa ser refinado.
