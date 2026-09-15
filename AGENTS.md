# AGENTS.md

Orientação para agentes de código (Claude Code, Codex, OpenCode e outros) trabalhando neste repositório.

## O que este repo é

Uma skill portátil escrita só em Markdown. O artefato de runtime é `SKILL.md`: o agente lê o frontmatter YAML e depois a receita. Não há build nem código executável.

## Arquivos

- `SKILL.md`: a skill. Frontmatter (`name`, `version`, `description`, `license`, `compatibility`, `allowed-tools`) seguido de princípio, entrada, receita, cotas, auditoria e tabela de racionalizações. É a fonte da verdade.
- `references/limpeza.md`: tabela de tiques de IA em português e o que a limpeza não pode mexer. É o passo 1 da receita; a skill não chama skill nenhuma para isso.
- `references/gramatica.md`: o que se escreve do pernambuquês (tu, -sse, visse, mainha, artigo, interjeições, falsos amigos).
- `references/lexico.md`: tabela termo, significado, registro, origem, exemplo. A coluna registro decide em que modo o termo entra; a coluna origem barra o que é de outro estado.
- `references/girias.md` e `references/formal.md`: as cotas aplicadas em três amostras cada.
- `README.md`: instalação, uso e histórico de versões.
- `.claude-plugin/`: manifesto de plugin e marketplace do Claude Code.

## Contrato de manutenção

- `version` vive em três lugares: frontmatter de `SKILL.md`, `.claude-plugin/plugin.json` e a seção de histórico do `README.md`. Sobem juntos. `marketplace.json` não tem versão de propósito.
- Toda mudança de comportamento em `SKILL.md` precisa de teste antes: rode o cenário em um subagente sem a skill, registre a falha literal, edite, rode de novo com a skill. Use texto que não esteja nas amostras de `references/`, porque os cenários originais viraram amostra.
- Termo novo no léxico só com fonte e origem. Termo de outro estado entra com registro `X` para o agente saber que é proibido, não some da tabela.
- A descrição do frontmatter diz só quando usar a skill, nunca resume o processo.
- Texto voltado a pessoa (README, references) não leva travessão nem lista com cabeçalho em negrito.

## Como testar

Cenários que já pegaram falha real: push de app em `girias`, e-mail de aviso em `formal`, diálogo de dois adolescentes do Recife, anúncio sem modo declarado. Falhas a vigiar: interjeição na abertura com `visse` no fecho, `você` e `tu` no mesmo texto, imperativo de `você` (`comece`) junto de `tua`, gíria de Ceará ou Bahia, `vosmecê` como formal, frase acrescentada só para dar sabor.
