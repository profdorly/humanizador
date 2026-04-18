# WARP.md

Este arquivo orienta o WARP (warp.dev) ao trabalhar no código deste repositório.

## O que é este repositório

Este repositório é uma **skill do Claude Code** implementada inteiramente em Markdown, adaptada para **português brasileiro**.

O artefato de runtime é o `SKILL.md`: o Claude Code lê o frontmatter YAML (metadados + ferramentas permitidas) e o prompt/instruções que vêm depois.

O `README.md` é voltado para humanos: instalação, uso e visão geral compacta dos padrões.

Esta skill é uma adaptação do projeto `humanizer` de Siqi Chen (MIT). Não é tradução literal — os padrões foram recalibrados a partir de textos de IA em PT-BR.

## Arquivos principais

- `SKILL.md`
  - Definição real da skill.
  - Começa com frontmatter YAML (`---` … `---`) contendo `name`, `version`, `description` e `allowed-tools`.
  - Depois do frontmatter vem o prompt do editor: a lista canônica e detalhada de padrões com exemplos, a seção "Quando NÃO corrigir" e três Full Examples.
- `README.md`
  - Instruções de instalação e uso.
  - Tabela-resumo dos 32 padrões e histórico de versões.
- `LICENSE`
  - MIT com dois avisos de copyright: Siqi Chen (2025) e o mantenedor do fork.

Ao mudar comportamento/conteúdo, trate `SKILL.md` como fonte da verdade e atualize `README.md` para manter a consistência.

## Comandos comuns

### Instalar a skill no Claude Code

Recomendado (clone direto na pasta de skills):

    mkdir -p ~/.claude/skills
    git clone https://github.com/profdorly/humanizador.git ~/.claude/skills/humanizador

Instalação/atualização manual (só o arquivo da skill):

    mkdir -p ~/.claude/skills/humanizador
    cp SKILL.md ~/.claude/skills/humanizador/

## Como "rodar" (Claude Code)

Invocar a skill:

- `/humanizador`, depois cole o texto.

## Fazer mudanças com segurança

### Versionamento (manter em sincronia)

- `SKILL.md` tem o campo `version:` no frontmatter YAML.
- `README.md` tem a seção "Histórico de versões".

Ao subir a versão, atualize os dois.

### Editando `SKILL.md`

- Preserve o frontmatter YAML com formatação e indentação válidas.
- Mantenha a numeração dos padrões estável, a menos que esteja renumerando intencionalmente (a tabela do `README.md` e os Full Examples referenciam a mesma numeração).
- Mantenha a seção "Quando NÃO corrigir" sincronizada com os itens de estilo (#21–24): as exceções de gênero estão distribuídas entre os dois lugares.

### Adicionando padrões PT-BR novos

- Se é tell realmente específico de PT-BR (ex: gerundismo, "a fim de"), inclua.
- Se é equivalente direto de algo do guia Wikipedia em inglês, confira se o comportamento em PT-BR é o mesmo antes de copiar.
- Evite incluir fenômenos que **não** são tells em PT-BR (ex: *"através de"* no sentido de "por meio de" — é aceito e não é sinal de IA).

### Documentando correções não óbvias

Se mudar o prompt para lidar com uma falha sutil (ex: reescrita errada recorrente, mudança de tom inesperada, falso positivo em determinado gênero), adicione uma nota curta no "Histórico de versões" do `README.md` descrevendo o que foi corrigido e por quê.

### Regra prática para o fork

Ao decidir entre manter algo do `humanizer` original ou substituir por algo específico de PT-BR:

- Se o fenômeno só faz sentido em inglês (ex: "delve", "tapestry", hyphenated word pairs como tell), substitua ou remova.
- Se é universal mas tem manifestação específica em PT-BR (ex: verbosidade, hedging, regra de três), adapte os exemplos.