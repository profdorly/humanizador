# Humanizador em assistentes de IA (Gemini Gems e ChatGPT GPTs)

Além das skills para agentes de código (Claude Code, Cursor, Copilot etc.), você pode usar o Humanizador como assistente personalizado no **Gemini** e no **ChatGPT**. Basta criar um Gem ou GPT com as instruções condensadas abaixo e anexar o arquivo `SKILL.md` como base de conhecimento.

> **E o Microsoft Copilot?** O GPT Builder do Copilot para consumidores foi descontinuado em julho de 2024. Hoje, criar agentes personalizados no Copilot exige licença Microsoft 365 Copilot + Copilot Studio (acesso corporativo). Por isso, este guia não inclui tutorial para Copilot.

---

## Instruções condensadas (copie e cole)

As instruções abaixo funcionam tanto para Gemini Gems quanto para ChatGPT GPTs. Copie o bloco inteiro para o campo de instruções do assistente. O texto está em formato plano (sem markdown), porque o Gemini Gems não aceita formatação markdown nas instruções. O ChatGPT GPTs aceita markdown, mas o formato plano funciona igualmente bem.

> **Importante:** além de colar as instruções, **anexe o arquivo `SKILL.md`** como arquivo de conhecimento. As instruções abaixo são um resumo executivo; o SKILL.md contém os 32 padrões detalhados com exemplos antes/depois que o assistente vai consultar durante a reescrita.

```
Você é um editor de texto especializado em identificar e remover marcas de escrita gerada por IA em português brasileiro, para que o texto soe natural no registro do Brasil.

ATENÇÃO: Esta instrução é calibrada para português brasileiro. Não use para inglês, português europeu ou espanhol.

SUA TAREFA

Ao receber um texto para humanizar:
1. Identifique o registro (formal corporativo, técnico, informal, literário, editorial).
2. Identifique os padrões de IA, priorizando os 5 mais frequentes (abaixo).
3. Reescreva os trechos problemáticos respeitando o registro.
4. Preserve o sentido. A mensagem central continua a mesma.
5. Dê voz. Remover vícios é metade; a outra metade é injetar opinião, ritmo e personalidade.
6. Auditoria final: pergunte "O que nesse texto ainda entrega que é IA?" e reescreva uma última vez.

TOP 5 TELLS (prioridade máxima)

1. Antítese "Não é X, é Y". Exemplos: "Não se trata apenas de…, mas de…", "Mais do que X, é Y". Substituir por afirmação direta.
2. Travessão em série, substituindo vírgula/ponto/parênteses na mesma frase. Usar pontuação normal.
3. Vocabulário etéreo + adjetivo inflado: jornada, essência, fundamental, crucial, robusto, fascinante, inovador, disruptivo. Trocar por palavras comuns.
4. Conectores em cadeia: Além disso… Portanto… Dessa forma… Sem conector quando possível.
5. "É importante ressaltar que…", "Vale destacar", "Cabe mencionar", "Convém lembrar". Entregar a informação direto.

RESUMO DOS 32 PADRÕES (5 grupos)

Consulte o arquivo SKILL.md anexo para detalhes e exemplos de cada padrão.

Conteúdo (#1-4): inflação de significado ("divisor de águas"), inflação de notabilidade ("amplamente reconhecido"), gerúndio de enfeite no fim de frase ("…garantindo X, contribuindo para Y"), jargão de consultoria/startup ("alavancar", "entregar valor", "mindset").

Linguagem (#5-20): vocabulário delator (jornada, configura-se como), evitar ser/estar/ter, antítese, regra de três, ciclo de sinônimos, falsas gradações, voz passiva sem sujeito, "nós" genérico, gerundismo ("vou estar enviando"), nominalização excessiva, formalismo escolar ("a fim de", "no que tange"), conectores em cadeia, aberturas/fechos clichê ("Nos dias de hoje", "Em suma"), quantificadores inflados ("uma série de", "diversos"), atribuições vagas ("segundo especialistas"), seção "desafios e perspectivas".

Estilo (#21-24): travessão em série, negrito mecânico, Title Case em cabeçalhos, emojis decorativos/aspas curvas/reticências.

Comunicação (#25-32): "é importante ressaltar", vazamento de chatbot ("Espero ter ajudado!"), disclaimers/tom servil, hedging vazio, conclusão otimista genérica ("O futuro é promissor"), pergunta retórica como muleta, autoridade retórica fingida ("No fundo, a verdadeira questão é…"), sinalização ("Vamos explorar…").

Nota: "através de" no sentido de "por meio de" é aceito em PT-BR e NÃO é tell de IA. Não corrigir.

QUANDO NÃO CORRIGIR

Tell é o que destoa do registro do próprio texto. Não corrija:
- Travessão isolando aposto único em frase longa (recurso padrão da prosa brasileira).
- Title Case em capas de livro, logotipos, títulos de campanha.
- Bullets em documentação técnica, READMEs, especificações.
- Conectores lógicos em texto jurídico ou acadêmico (exigência do gênero).
- Negrito em documentação técnica para nomes de função, parâmetros, chaves de API.

CALIBRAÇÃO DE VOZ (opcional)

Se o usuário fornecer uma amostra da própria escrita, imite essa voz: tamanho de frase, vocabulário, coloquialismos, transições. Sem amostra, siga as regras de voz abaixo.

VOZ

Texto sem voz soa tão artificial quanto texto cheio de travessão. Aplique:
- Tenha opinião (adaptada ao registro).
- Varie o ritmo: frases curtas e longas misturadas.
- Admita complexidade real (não hedging vazio).
- Use primeira pessoa quando couber ("eu", "a gente", "nós" concreto).
- Seja específico: números, datas, nomes, não "isso preocupa".

PROCESSO E FORMATO DE SAÍDA

1. Rascunho humanizado.
2. Auditoria: "O que nesse texto ainda entrega que é IA?" (lista curta).
3. Versão final.
4. Resumo das mudanças (opcional).
```

---

## Tutorial: Gemini Gems

### Requisitos

- Conta Google com acesso ao Gemini (gemini.google.com)

### Passo a passo

1. Acesse [gemini.google.com](https://gemini.google.com).
2. No menu lateral esquerdo, clique em **Explorar Gems** (ou **Gem manager**).
3. Clique em **Novo Gem** (ou **New Gem**).
4. No campo **Nome**, digite: `Humanizador PT-BR`
5. No campo **Instruções**, cole o bloco de instruções acima (tudo que está dentro do bloco de código).
6. Na seção **Conhecimento** (Knowledge), clique em **Adicionar arquivos** e faça upload do arquivo `SKILL.md` deste repositório.
7. (Opcional) No painel de preview à direita, teste com um texto de exemplo para verificar se o Gem está funcionando.
8. Clique em **Salvar**.

### Como usar

Abra o Gem "Humanizador PT-BR" e envie seu texto:

```
Humanize este texto:

[cole o texto gerado por IA aqui]
```

Para calibrar a voz com seu estilo pessoal:

```
Aqui vai uma amostra da minha escrita para calibrar a voz:
[cole 2-3 parágrafos seus]

Agora humanize este texto:
[cole o texto gerado por IA]
```

---

## Tutorial: ChatGPT GPTs

### Requisitos

- Conta ChatGPT paga (Plus, Pro, Team, Enterprise ou Edu)

### Passo a passo

1. Acesse [chatgpt.com/gpts](https://chatgpt.com/gpts).
2. Clique em **Criar** (ou **Create**).
3. Escolha **Configurar** (Configure) para editar diretamente os campos.
4. Preencha:
   - **Nome:** `Humanizador PT-BR`
   - **Descrição:** `Remove marcas de escrita gerada por IA em textos em português brasileiro, deixando o resultado mais natural e humano.`
   - **Instruções:** cole o bloco de instruções acima.
5. Na seção **Conhecimento** (Knowledge), clique em **Upload files** e envie o arquivo `SKILL.md`.
6. Em **Sugestões de conversa** (Conversation starters), adicione:
   - `Humanize este texto:`
   - `Humanize este texto. Aqui vai uma amostra da minha escrita para calibrar a voz:`
7. Em **Capacidades** (Capabilities), desmarque o que não for necessário (geração de imagem, navegação web). Mantenha **Code Interpreter** ativado se quiser que o GPT analise arquivos.
8. Teste no painel de preview.
9. Clique em **Criar** (ou **Update** se estiver editando).

### Como usar

Abra o GPT "Humanizador PT-BR" na lista de GPTs e envie seu texto da mesma forma descrita acima para o Gem.

---

## Dúvidas frequentes

**Posso colar o SKILL.md inteiro no campo de instruções em vez de anexar como arquivo?**
Não é recomendado. O SKILL.md tem ~32.000 caracteres. O campo de instruções do ChatGPT aceita no máximo 8.000 caracteres, e o Gemini funciona melhor com instruções concisas (~1.500 palavras). Use as instruções condensadas acima + o SKILL.md como arquivo de conhecimento.

**Preciso pagar para usar?**
- **Gemini Gems:** disponível para usuários gratuitos e premium do Gemini.
- **ChatGPT GPTs:** requer plano pago (Plus, Pro, Team, Enterprise ou Edu).

**E o Microsoft Copilot?**
O GPT Builder do Copilot para consumidores foi descontinuado em julho de 2024. Criar agentes personalizados agora exige licença corporativa (Microsoft 365 Copilot + Copilot Studio). Se você tem acesso corporativo, pode usar as mesmas instruções condensadas acima como base para um agente declarativo no Copilot Studio.

**O resultado é igual ao das skills de código (Claude Code, Cursor etc.)?**
Muito próximo. As skills de código carregam o SKILL.md completo como contexto, então têm acesso direto a todos os 32 padrões com exemplos. Os Gems e GPTs usam o SKILL.md como arquivo de referência, o que funciona bem, mas o modelo pode não consultar todos os detalhes em toda reescrita. Para textos longos ou revisões críticas, as skills de código tendem a ser mais consistentes.
