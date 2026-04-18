# Humanizador

Skill para Claude Code e OpenCode que remove marcas de escrita gerada por IA em textos em **português brasileiro**, deixando o resultado mais natural e humano no registro do Brasil.

Esta skill é uma adaptação do projeto humanizer (https://github.com/blader/humanizer). Não é tradução literal: os padrões foram recalibrados a partir de textos de IA em PT-BR, e o guia original em inglês (baseado na Wikipedia) foi substituído por referências brasileiras.

## Instalação

### Claude Code

Clone direto na pasta de skills do Claude Code:

    mkdir -p ~/.claude/skills
    git clone https://github.com/profdorly/humanizador.git ~/.claude/skills/humanizador

Ou copie só o arquivo da skill, se já tem o repo clonado:

    mkdir -p ~/.claude/skills/humanizador
    cp SKILL.md ~/.claude/skills/humanizador/

### OpenCode

    mkdir -p ~/.config/opencode/skills
    git clone https://github.com/profdorly/humanizador.git ~/.config/opencode/skills/humanizador

> **Nota:** o OpenCode também lê `~/.claude/skills/`, então um clone único em `~/.claude/skills/humanizador/` funciona para os dois.

### Warp (warp.dev)

O Warp pode usar o `WARP.md` deste repositório como orientação ao trabalhar no código. Para usar a skill no Warp, siga o fluxo padrão do Claude Code (o Warp usa o mesmo sistema de skills):

    mkdir -p ~/.claude/skills
    git clone https://github.com/profdorly/humanizador.git ~/.claude/skills/humanizador

Depois invoque com `/humanizador` no Warp.

## Uso

### Invocação direta

    /humanizador
    [cole seu texto aqui]

Ou peça em linguagem natural:

    Humanize este texto: [seu texto]

### Calibração de voz (opcional)

Para que a reescrita imite seu estilo pessoal, forneça uma amostra:

    /humanizador

    Aqui vai uma amostra da minha escrita para calibrar a voz:
    [cole 2-3 parágrafos seus]

    Agora humanize este texto:
    [cole o texto gerado por IA]

A skill analisa ritmo, vocabulário e cacoetes da amostra e aplica isso na reescrita, em vez de produzir uma versão "limpa" genérica.

## Visão geral

A skill detecta e corrige **32 padrões** de IA específicos do PT-BR, organizados em cinco grupos:

1. **Conteúdo** — inflação de importância, notabilidade vaga, gerúndio de enfeite, jargão de consultoria.
2. **Linguagem e gramática** — vocabulário delator, antítese, regra de três, gerundismo, nominalização, formalismo escolar, conectores em cadeia, dêixis temporal vaga, quantificadores inflados.
3. **Estilo** — travessão em série, negrito mecânico, Title Case, emojis decorativos.
4. **Comunicação** — vazamento de chatbot, tom servil, disclaimers de corte de treinamento.
5. **Muletas e hedging** — "é importante ressaltar", pergunta retórica, autoridade retórica fingida, sinalização.

Antes de corrigir, a skill aplica a seção **"Quando NÃO corrigir"** como filtro de falso positivo: travessão legítimo, Title Case em capa de livro, aspas curvas editoriais, bullets em documentação técnica etc. não são corrigidos.

A skill faz **duas passadas**: rascunho humanizado → auditoria *"o que ainda entrega que é IA?"* → versão final.

## Top 5 tells em PT-BR

Se você tiver pouco tempo de revisão, ataque esses primeiro:

1. **Antítese "Não é X, é Y"** / "Não se trata apenas de…, mas de…"
2. **Travessão em série** substituindo vírgula/ponto/parênteses
3. **Vocabulário etéreo + adjetivo inflado** (jornada, essência, fundamental, crucial, robusto)
4. **Conectores em cadeia** (Além disso… Portanto… Dessa forma…)
5. **"É importante ressaltar que…"** e companhia

## Tabela-resumo dos 32 padrões

### Conteúdo

| # | Padrão | Evitar | Preferir |
|---|--------|--------|----------|
| 1 | Inflação de significado | "representa um marco", "divisor de águas" | Datas e números |
| 2 | Inflação de notabilidade | "amplamente reconhecida, vasta experiência" | Fato com ano |
| 3 | Gerúndio de enfeite | "…garantindo X, contribuindo para Y" | Ponto + frase nova |
| 4 | Jargão consultoria/startup BR | "alavancar", "entregar valor", "mindset" | Verbo concreto |

### Linguagem

| # | Padrão | Evitar | Preferir |
|---|--------|--------|----------|
| 5 | Vocabulário delator | jornada, fundamental, configura-se como | "é", "tem", palavra comum |
| 6 | Evitar "ser/estar/ter" | "configura-se como" | "é" |
| 7 | Antítese "Não é X, é Y" | "Mais do que ferramenta, é parceiro" | Afirmação direta |
| 8 | Regra de três e paralelismo | Trincas; "Ele fez. Ele fez. Ele fez." | Número natural de itens |
| 9 | Ciclo de sinônimos | protagonista → personagem → figura central | Repetir quando for mais claro |
| 10 | Falsas gradações | "do Big Bang à consciência artificial" | Lista sem escala falsa |
| 11 | Voz passiva sem sujeito | "Resultados são preservados" | "O sistema preserva…" |
| 12 | "Nós" genérico | "enquanto sociedade" | "Você" ou "a empresa" |
| 13 | Gerundismo | "vou estar enviando" | "envio" |
| 14 | Nominalização excessiva | "realização da tomada de decisão" | "para decidir" |
| 15 | Formalismo escolar | "a fim de", "haja vista", "no que tange a" | "para", "porque", "sobre" |
| 16 | Conectores em cadeia | Além disso… Portanto… Dessa forma… | Sem conector quando possível |
| 17 | Aberturas/fechos clichê + dêixis vaga | "Nos dias de hoje…", "Em suma…" | Fato datado |
| 18 | Quantificadores inflados | "uma série de", "diversos", "múltiplos" | Número exato |
| 19 | Atribuições vagas | "segundo especialistas" | Estudo com ano e N |
| 20 | "Desafios e perspectivas" | "Apesar dos avanços… perspectivas promissoras" | Fato específico |

### Estilo

| # | Padrão | Evitar | Preferir |
|---|--------|--------|----------|
| 21 | Travessão em série | "A — frase — intercalada —" | Vírgula, ponto, parênteses |
| 22 | Negrito mecânico | **Bold** em frases inteiras | Só em termos técnicos |
| 23 | Title Case | "Negociações Estratégicas E Parcerias" | "Negociações estratégicas e parcerias" |
| 24 | Emojis, aspas curvas, reticências | 🚀 bullets; aspas curvas em doc bruto | Texto corrido |

### Comunicação

| # | Padrão | Evitar | Preferir |
|---|--------|--------|----------|
| 25 | "É importante ressaltar" | "Vale destacar que…" | Entrega direta |
| 26 | Vazamento de chatbot | "Espero ter ajudado!" | Só o conteúdo |
| 27 | Disclaimers + tom servil | "embora os detalhes sejam escassos" | Fato ou silêncio |
| 28 | Hedging vazio vs dúvida honesta | "pode-se eventualmente talvez" | "provavelmente X, embora…" |
| 29 | Conclusão otimista genérica | "O futuro é promissor" | Plano concreto com data |
| 30 | Pergunta retórica | "Você já parou para pensar…?" | Afirmação |
| 31 | Autoridade retórica fingida | "No fundo, a verdadeira questão é…" | "A pergunta é…" |
| 32 | Sinalização + cabeçalho com aquecimento | "Vamos mergulhar em…" | Começar pelo conteúdo |

> **Nota importante:** *"através de"* no sentido de "por meio de" é amplamente aceito em PT-BR e **não** é tell de IA. Não corrigir.

## Exemplo

**Antes (cara de IA):**
> No mundo atual, em um cenário cada vez mais marcado pela transformação digital, a Inteligência Artificial configura-se como um divisor de águas — um marco que redefine a jornada de aprendizagem dos profissionais.
>
> É importante ressaltar que não se trata apenas de uma ferramenta, mas de um verdadeiro parceiro estratégico, capaz de potencializar resultados, alavancar a produtividade e entregar valor em todas as etapas.
>
> Em suma, o futuro é promissor. As possibilidades são infinitas.

**Depois (humanizado):**
> Esta apostila é o material de apoio da sessão 2. Funciona melhor como consulta depois do encontro ao vivo — não precisa ler do começo ao fim.
>
> O foco é engenharia de prompt aplicada ao trabalho. Os frameworks que a gente vai usar (C.I.F.E., Entrevista Reversa, Chain-of-Thought, Prompt Chaining) são os mesmos que uso com clientes corporativos todo mês.

O `SKILL.md` traz ainda dois exemplos adicionais: um em registro **formal corporativo** (comunicado executivo) e um em registro **técnico** (README de biblioteca).

## Referências

- Wikipedia: Signs of AI writing — https://en.wikipedia.org/wiki/Wikipedia:Signs_of_AI_writing — fonte do projeto original
- Envox, "Os 12 maiores vícios de linguagem de IA em 2026"
- Advoco Brasil, "Os vícios linguísticos das IAs"
- Comunidade O Novo Mercado, "9 vícios de escrita que dão aquele cheirinho de IA"
- Na Prática, sobre o estudo do Instituto Max Planck
- BBC News Brasil, "Dá para identificar texto gerado por IA?"

## Histórico de versões

- **0.2.0** — Adicionada seção "Quando NÃO corrigir"; 3 Full Examples em registros diferentes (informal, formal, técnico); novos tells (ao invés de / em vez de, dêixis temporal vaga, quantificadores inflados, paralelismo forçado); Top 5 como ponteiros; exceções de gênero em Title Case e aspas curvas; seções em sentence case.
- **0.1.0** — Reescrita inicial em PT-BR a partir do `humanizer` v2.5.1 de Siqi Chen. Substituída base Wikipedia EN por padrões observados em textos de IA em PT-BR.

## Licença

MIT.

Esta é uma adaptação para português brasileiro do projeto humanizer (https://github.com/blader/humanizer) (© 2025, MIT). O aviso de copyright original está preservado no arquivo `LICENSE`.