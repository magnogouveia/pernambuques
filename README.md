# Pernambuquês

Skill portátil que reescreve um texto pronto na voz de Pernambuco. É só Markdown, então roda em qualquer harness que carregue instruções no formato de skill (Claude Code, Codex, OpenCode e outros).

Dois registros:

- `girias`: fala jovem e de rua da Região Metropolitana do Recife. `tu` com verbo na 3ª pessoa, léxico da cidade (massa, de rosca, bizu, pala), `visse?` só no fecho.
- `formal`: norma culta com marca regional. Tratamento do original mantido, uma troca de léxico tradicional por parágrafo (findar, ruma, aperreio, arrodear), zero gíria e zero arcaísmo.

A regra central é dosagem. Sem a skill, o modelo abre com "oxe" e fecha com "visse" em todo texto, mistura `tu` com `você`, puxa gíria do Ceará e da Bahia e trata "vosmecê" como formal. A skill troca isso por cotas contadas, uma tabela de léxico com origem e uma auditoria que pergunta se um recifense leria aquilo como natural.

## Instalação

### Skills CLI

```bash
npx skills add magnogouveia/pernambuques
```

Atualizar:

```bash
npx skills update pernambuques
```

Instalar em todos os harnesses configurados:

```bash
npx skills add magnogouveia/pernambuques --agent '*'
```

### Plugin do Claude Code

```
/plugin marketplace add magnogouveia/pernambuques
/plugin install pernambuques@pernambuques
```

A skill passa a responder por `/pernambuques:pernambuques`.

### Manual

```bash
git clone https://github.com/magnogouveia/pernambuques.git ~/.claude/skills/pernambuques
```

Ou copie `SKILL.md` e a pasta `references/` para onde o seu harness espera skills.

## Uso

Com modo declarado:

```
/pernambuques girias

[texto]
```

```
/pernambuques formal

[texto]
```

Sem modo, a skill infere: e-mail, nota e aviso institucional caem em `formal`; push, anúncio, post, mensagem e diálogo caem em `girias`. Ela declara o modo na primeira linha da entrega e lista as marcas que usou na última, para você cortar o que não quiser.

Exemplo em `girias`:

> Original: "Sua redação foi corrigida. Veja o feedback no app."
>
> Reescrita: "Tua redação já tá corrigida. Vai lá no app ver o feedback, visse?"

Exemplo em `formal`:

> Original: "Se tiver qualquer dúvida sobre a cobrança, responda este e-mail que a gente ajuda."
>
> Reescrita: "Qualquer dúvida sobre a cobrança, sem aperreio: responda este e-mail que a gente ajuda."

Zero marca é resposta válida. Se nenhuma troca soaria natural, o texto volta com pronome ajustado e `marcas: nenhuma`. Marca enfiada para cumprir cota é o erro.

## Limpeza antes da voz

A skill é autocontida: não depende de nenhuma outra skill. Antes de aplicar qualquer marca regional, ela passa o original pela tabela de tiques de IA em `references/limpeza.md` (travessão de aposto, significância inflada, promocionalês, atribuição vaga, regra de três, paralelismo negativo, fecho resumo, vocabulário de IA). A correção é só do tique: do original ao final, o texto guarda o mesmo número de parágrafos e frases, o mesmo sentido, nenhum travessão e nenhum emoji novo. Quando não há tique, a entrega registra `limpeza: nenhuma`.

## O que entra e o que não entra

| | girias | formal |
|---|---|---|
| `tu` | 3ª pessoa, sempre (`tu vai`, `manda`) | só se o original já tinha |
| `visse?` | 0 ou 1, na última frase | 0 |
| interjeição (oxe, eita, vixe) | 1 por parágrafo; em diálogo, 1 a cada 3 falas | 0 |
| gíria lexical | 1 por frase | 0 |
| léxico tradicional | dentro da cota de gíria | 1 por parágrafo, só trocando palavra existente |
| vocativo (bicho, rapaz, mermão) | só se o original tinha vocativo | 0 |
| grafia de fala (tá, pra, tô) | livre | 0 |
| grafia de sotaque (num, mermo, pexe) | só em fala de personagem | 0 |
| fora de Pernambuco (égua, sussa, migué, vosmecê) | 0 | 0 |

O léxico completo, com registro e origem de cada termo, está em [`references/lexico.md`](references/lexico.md). A gramática do que se escreve (e do que não se escreve, como o chiado do /s/) está em [`references/gramatica.md`](references/gramatica.md).

## Como foi feita

TDD de skill: 13 rodadas de baseline em subagente sem a skill, com as falhas registradas literalmente; depois a skill escrita para fechar essas falhas; depois 16 rodadas com a skill até as saídas convergirem. Os cenários originais viraram amostras em `references/`, então teste novo pede texto inédito. Detalhes em [`AGENTS.md`](AGENTS.md).

Fontes do estudo: Wikipédia (Dialeto recifense), Marco Zero (O dialeto que só os recifenses falam), Elon.io (Pernambucano), Janelas Abertas e KondZilla (gírias do Recife), Dicionário Popular, Made in Brasilis, Singrando Horizontes (pe-az.com.br) e Manuel Bandeira, Evocação do Recife.

## Histórico de versões

### 1.1.0

A skill deixou de chamar o humanizer como sub-skill obrigatória e passou a fazer a limpeza de tiques de IA sozinha, pela tabela nova em `references/limpeza.md`, que virou o passo 1 da receita. A entrega ganhou a linha `limpeza:`.

### 1.0.0

Primeira versão. Dois modos, tabela de cotas, léxico com 90 termos marcados por registro e origem, quatro references, tabela de racionalizações vinda do baseline.

## Licença

MIT
