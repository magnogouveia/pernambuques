---
name: pernambuques
version: 1.1.0
description: Use quando pedirem para reescrever um texto pronto "em pernambuquês", "deixar pernambucano", dar voz recifense, sotaque de Pernambuco, gírias do Recife, ou um "pernambucano formal/culto" em copy, push, e-mail, marketing, diálogo de personagem ou mensagem; também quando o usuário digitar /pernambuques girias ou /pernambuques formal.
license: MIT
compatibility: any-agent
allowed-tools:
  - Read
  - Write
  - Edit
  - AskUserQuestion
---

# Pernambuquês: reescrever na voz de Pernambuco

## Princípio

Pernambucano de verdade não é "oxe" na abertura e "visse" no fecho. É o `tu` sem concordância e a palavra da cidade no lugar da neutra, uma de cada vez. Quem lê no Recife não pode sentir turista imitando. Real vence marcado: menos marca e natural é melhor que a cota cheia.

## Entrada

Texto pronto + modo. `girias` = fala jovem e de rua da Região Metropolitana do Recife. `formal` = norma culta com marca regional. Sem modo: e-mail, nota, aviso institucional ⇒ `formal`; push, anúncio, post, mensagem, diálogo ⇒ `girias`; ambíguo ⇒ AskUserQuestion. Primeira linha da entrega: `modo: girias` ou `modo: formal`.

## Receita

1. Limpe os tiques de IA do original pela tabela de `references/limpeza.md`, sempre, mesmo quando o texto parece limpo. Corrige só o tique. Do original ao final, o texto guarda o mesmo número de parágrafos e frases, o mesmo sentido, nenhum travessão e nenhum emoji novo. Sem tique achado, a entrega diz `limpeza: nenhuma`.
2. Marque no original cada palavra ou expressão neutra com equivalente de sentido em `references/lexico.md` no registro do modo. Só essas viram marca. Não entra frase nova nem vocativo novo. Se nenhuma troca soaria natural na boca de um recifense, o texto volta sem marca lexical e a entrega diz `marcas: nenhuma`. Marca enfiada para cumprir cota é o erro, não a ausência dela.
3. Pronome. `girias`: `tu` com verbo na 3ª pessoa (`tu vai`, `tu mandou`), imperativo idem (`manda`, `começa`, nunca `mande`, `comece`), `te/teu/tua`, no texto inteiro; `você` e `tu vais` não aparecem. `formal`: mantém o tratamento do original (`você`, `senhor`, `a gente`).
4. Aplique as cotas da tabela. Marca = gíria, interjeição, tag ou vocativo.
5. Rascunho, depois as três perguntas da auditoria, depois o final.
6. Entrega: linha `modo:`, texto final, linha `limpeza:` com o que foi corrigido, linha `marcas:` listando cada marca usada.

## Cotas

| | girias | formal |
|---|---|---|
| `tu` | 3ª pessoa, sempre | só se o original já tinha `tu` |
| `visse?` | 0 ou 1, na última frase, com `?` | 0 |
| interjeição (oxe, eita, vixe) | ≤1 por parágrafo; em diálogo ≤1 a cada 3 falas | 0 |
| gíria lexical (massa, de rosca, bizu, pala) | ≤1 por frase | 0 |
| léxico tradicional (arrodear, ruma, aperreio, findar) | dentro da cota de gíria | ≤1 por parágrafo, só trocando palavra existente |
| vocativo (bicho, rapaz, mermão, boy) | só se o original tinha vocativo | 0 |
| grafia de fala (`tá`, `pra`, `tô`) | livre | 0 |
| grafia de sotaque (num, mermo, pexe, oxi) | só em fala de personagem | 0 |
| fora de PE (égua, sussa, migué, ó paí, vosmecê, Vossa Mercê, cabra como vocativo) | 0 | 0 |

## Auditoria

1. Um recifense leria como natural ou como turista imitando?
2. Cada marca trocou uma palavra do original ou foi enfiada?
3. O texto abre com interjeição e fecha com `visse`? Se sim, é o sanduíche: tire um dos dois.

## Racionalizações vistas sem a skill

| Desculpa | Realidade |
|---|---|
| "Oxe e visse abrem e fecham a frase" | Sanduíche oxe…visse saiu em 13 de 13 sem a skill. Tell número um. |
| "Vosmecê / Vossa Mercê é culto pernambucano" | É arcaico de cordel. Culto regional usa `você`/`senhor` e léxico tradicional. |
| "Cabra é vocativo típico" | Sertão e ficção. Adolescente do Recife diz bicho, rapaz, mermão, boy. |
| "Égua e sussa dão tom jovem" | Égua é Ceará e Pará; sussa é Sudeste. Coluna origem do léxico. |
| "Arretado esperando por você dá sabor" | Frase nova. Reescrita não acrescenta. |
| "Sem exagerar a dosagem" (4 marcas em 4 frases) | Cota se conta, não se sente. |
| "Nenhuma palavra bate literalmente com o léxico" | Equivalência é de sentido ("volume acima do comum" ⇒ "uma ruma de"). Se nada cabe, zero marca. |
| "Já estava limpo, não havia o que corrigir" | A limpeza roda em todo texto e registra o que achou, nem que seja `limpeza: nenhuma`. |

## Referências

`references/limpeza.md` (tiques de IA e o que a limpeza não pode mexer) · `references/gramatica.md` (tu, -sse, visse, mainha, artigo, interjeições, falsos amigos) · `references/lexico.md` (termo, registro, origem) · `references/girias.md` e `references/formal.md` (cotas aplicadas em três amostras cada).
