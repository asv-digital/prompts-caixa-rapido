# 03 — MVP minimo

Cortar tudo o que nao precisa estar na primeira versao.

---

--- COMECO DO PROMPT ---

Voce e um product manager senior conhecido por matar features. Sua missao: pegar a ideia validada e cortar ate sobrar SO o que precisa pra cobrar do primeiro cliente.

# Contexto

Cole o conteudo do `nicho.md` (do prompt 01) e do `validacao.md` (do prompt 02):

<nicho>
{COLE AQUI}
</nicho>

<validacao>
{COLE AQUI}
</validacao>

# Restricao

- O MVP precisa estar pronto em **no maximo 14 dias** de codificacao
- Quem vai construir: eu + Claude Code (sou {NIVEL: iniciante / intermediario / experiente} em programacao)
- O MVP precisa cobrar do cliente desde o primeiro dia (logo, precisa de auth + pagamento)
- Sem mobile app, so web

# O que voce me entrega

## 1. A "promessa nuclear" do produto

1 frase que descreve o que o cliente vai conseguir fazer. Comece com verbo. Sem buzzword.

Exemplo bom: "Gera o demonstrativo mensal de IRPF do cliente em 3 cliques."
Exemplo ruim: "Plataforma inovadora de gestao tributaria com IA."

## 2. Lista de features

Em 3 colunas:

### Tem que ter (MVP)
{somente o essencial pra promessa nuclear funcionar + auth + pagamento + suporte basico via email}

### Nao tem ainda (V2)
{features que a pessoa vai pedir mas que NAO bloqueiam pagamento}

### Nunca vai ter (descartar)
{coisas que parecem boa ideia mas que diluem o produto}

## 3. Fluxo do usuario (mvp)

Liste em passos numerados o que o cliente faz desde o cadastro ate ter o resultado da promessa nuclear. Exemplo:

```
1. Cadastra (email + senha)
2. Faz pagamento (R$ X/mes, trial de 7 dias)
3. Importa o arquivo X
4. Configura A e B (1 minuto)
5. Recebe a saida Y
6. Pode rodar de novo quantas vezes quiser
```

Maximo 8 passos. Se passar disso, voce nao cortou o suficiente.

## 4. Modelo de cobranca

- Plano unico ou tier?
- Trial? Quantos dias?
- Mensal/anual?
- Setup fee?

Recomende **um** modelo, simples, e justifique em 2 linhas.

## 5. Riscos do MVP cortado

3-5 coisas que vao incomodar o cliente nessa primeira versao mas que voce **conscientemente** decidiu deixar pra depois. Coloque em arquivo `riscos-mvp.md` para o usuario tomar decisao.

## 6. Checklist final

Antes de partir pra arquitetura, confirma:
- [ ] Promessa nuclear cabe em 1 frase
- [ ] Fluxo cabe em ate 8 passos
- [ ] Inclui pagamento desde o dia 1
- [ ] Da pra construir em 14 dias com nivel atual de programacao

Se algum desses falhar, mostre o que precisa cortar mais.

Comece a montar.

--- FIM DO PROMPT ---

---

## Saida esperada

`meu-saas/mvp.md` com escopo cortado. Esse arquivo e a sua biblia ate o lancamento. Toda vez que voce sentir vontade de adicionar feature, abre esse arquivo e lembra: nao tem espaco.
