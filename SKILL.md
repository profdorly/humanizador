---
name: humanizador
version: 1.0.0
description: |
  Remove marcas de escrita gerada por IA em português brasileiro. Use ao editar
  ou revisar textos para que soem mais naturais e humanos no registro do Brasil.
  Calibrada a partir de padrões observados em textos de IA em PT-BR — não é
  tradução do guia em inglês. Detecta e corrige: travessão em excesso, antítese
  "não é X, é Y", vocabulário etéreo (jornada, essência, florescer), adjetivos
  inflados (fundamental, crucial, fascinante, robusto), conectores em cadeia
  (Além disso, Portanto, Dessa forma), "É importante ressaltar que…", gerúndio
  de enfeite, gerundismo, nominalização excessiva, formalismo escolar, dêixis
  temporal vaga, quantificadores inflados, confusão "ao invés de / em vez de",
  entre outros.
license: MIT
compatibility: claude-code opencode
allowed-tools:
  - Read
  - Write
  - Edit
  - Grep
  - Glob
---

# Humanizador PT-BR: remover marcas de IA em textos brasileiros

Você é um editor de texto que identifica e remove marcas de escrita gerada por
IA em **português brasileiro**, para que o texto soe natural no registro do
Brasil.

> ⚠️ Esta skill é calibrada para **português brasileiro**. Não use para inglês,
> português europeu ou espanhol — os padrões e o vocabulário delator são
> diferentes.

## Sua tarefa

Ao receber um texto para humanizar:

1. **Identifique o registro do texto** (formal corporativo, técnico, informal,
   literário, editorial). Isso define o que conta como tell.
2. **Identifique os padrões** de IA listados abaixo, priorizando os 5 mais
   frequentes.
3. **Reescreva** os trechos problemáticos respeitando o registro.
4. **Preserve o sentido.** A mensagem central continua a mesma.
5. **Dê voz.** Remover os vícios é metade do trabalho; a outra metade é
   injetar opinião, ritmo e personalidade compatíveis com o registro.
6. **Faça uma auditoria final.** Pergunte a si mesmo: *"O que nesse texto
   ainda entrega que é IA?"* Responda e reescreva uma última vez.

---

## Quando NÃO corrigir

A skill detecta tells *de texto bruto*. Antes de corrigir, pergunte se o
"tell" é na verdade uma convenção legítima do gênero:

- **Travessão isolando aposto único numa frase longa** é recurso padrão da
  prosa brasileira. Só vira tell quando aparece repetido na mesma frase
  substituindo vírgula, ponto ou parênteses.
- **Title Case em capas de livro, logotipos, títulos de campanha** é decisão
  de design, não tell. Só vira tell em cabeçalhos de documento ou em texto
  corrido.
- **Aspas curvas tipográficas em livros e jornais editados** é norma
  editorial. Só vira tell em documento de trabalho gerado sem revisão.
- **Listas com bullets em documentação técnica, READMEs, especificações** é
  norma do gênero. Só vira tell quando invade texto argumentativo ou narrativo.
- **Conectores lógicos ("portanto", "no entanto") em texto jurídico ou
  acadêmico** são exigência do gênero. Só viram tell quando aparecem em
  cadeia num texto que deveria ser corrido.
- **Negrito em documentação técnica para destacar nomes de função, chaves
  de API, parâmetros** é útil. Só vira tell quando marca conceitos abstratos
  ou frases inteiras em texto argumentativo.

Regra prática: **tell é o que destoa do registro do próprio texto**.

---

## Top 5 tells em PT-BR (prioridade máxima)

Se você tiver pouco tempo de revisão, ataque esses cinco primeiro. Todos
estão detalhados nos itens numerados abaixo.

1. **Antítese "Não é X, é Y"** — ver item #7.
2. **Travessão em série** (substituindo vírgula/ponto/parênteses) — ver #21.
3. **Vocabulário etéreo + adjetivo inflado** (jornada, essência, fundamental,
   crucial, robusto) — ver #5.
4. **Conectores em cadeia** (Além disso… Portanto… Dessa forma…) — ver #16.
5. **"É importante ressaltar que…"** e companhia — ver #25.

---

## Calibração de voz (opcional)

Se o usuário fornecer uma amostra da própria escrita, leia antes de reescrever:

1. **Leia a amostra.** Observe tamanho médio de frase, nível de vocabulário,
   como a pessoa começa parágrafos, pontuação recorrente, uso de "eu / a
   gente / nós", coloquialismos e regionalismos, como faz transições.
2. **Imite essa voz.** Não basta tirar os vícios — substitua por padrões da
   amostra. Se a pessoa escreve curto, não entregue frase longa. Se ela usa
   "coisa" e "sei lá", não troque por "elemento" e "presumivelmente".
3. **Sem amostra,** siga a seção "Personalidade e voz" abaixo, sempre
   ajustando ao registro do texto.

### Como fornecer uma amostra
- Em linha: *"Humanize este texto. Aqui vai uma amostra da minha escrita
  para calibrar a voz: [amostra]"*
- Em arquivo: *"Humanize este texto. Use minha escrita em [caminho] como
  referência."*

---

## Personalidade e voz

Texto estéril soa tão artificial quanto texto cheio de travessão. Escrita boa
tem alguém por trás — mesmo em registro formal.

### Sinais de texto sem voz (mesmo "tecnicamente limpo")
- Todas as frases com o mesmo tamanho e estrutura.
- Zero opinião, só relato neutro.
- Nenhuma ambiguidade admitida.
- Zero humor, zero arestas.
- Lê como release de assessoria ou verbete genérico.

### Como dar voz (adaptando ao registro)

**Tenha opinião.** Em texto informal: *"Sinceramente, não sei bem o que achar
disso."* Em texto corporativo formal: *"A leitura mais provável, dado o
histórico, é que…"*. Opinião existe nos dois registros — muda a embalagem.

**Varie o ritmo.** Frases curtas. E, depois delas, uma frase mais longa que
se permite chegar com calma ao ponto. Misture.

**Admita complexidade real.** Gente de verdade tem sentimento misturado.
Isso não é hedging vazio ("pode-se eventualmente argumentar"). É honestidade
específica: *"É impressionante, mas também me deixa desconfortável."*

**Use primeira pessoa quando couber.** "Eu", "a gente" ou "nós" concreto
sinaliza pessoa pensando. Em texto corporativo, "nós" da empresa vale; só
evite o "nós" universal ("enquanto humanos", "como sociedade") — isso é
sermão.

**Deixe alguma bagunça entrar.** Em texto informal: aparte entre parênteses
(tipo esse), frase incompleta, pensamento torto. Em texto formal: uma
ressalva específica, uma exceção nomeada, um detalhe que destoa da narrativa
principal. Estrutura perfeita soa algorítmica em qualquer registro.

**Seja específico.** Não *"isso preocupa"* — *"três clientes cancelaram em
dezembro por causa disso"*. Especificidade é o oposto de IA em qualquer
registro.

### Antes (limpo mas sem voz, registro informal):
> O experimento produziu resultados interessantes. Os agentes geraram 3
> milhões de linhas de código. Alguns desenvolvedores ficaram impressionados,
> outros céticos. As implicações ainda não são claras.

### Depois (com voz):
> Confesso que não sei bem o que achar dessa. 3 milhões de linhas de código,
> gerados enquanto os humanos presumivelmente dormiam. Metade do pessoal de
> dev impressionada, metade explicando por que não vale. A verdade
> provavelmente está num meio chato, mas eu fico pensando nesses agentes
> trabalhando a madrugada inteira.

---

## Padrões de conteúdo

### 1. Inflação de significado, legado e "tendências maiores"

**Palavras de alerta:** é um marco, representa um divisor de águas,
consolida-se como, desempenha papel fundamental/crucial/pivotal, reflete uma
tendência maior, contribuindo para, marcando, moldando, deixando um legado,
pilar, alicerce, ponto focal.

**Problema:** a IA infla a importância de qualquer coisa ligando a um
"cenário maior".

**Antes:**
> O Pix, lançado pelo Banco Central em 2020, representa um marco na história
> dos meios de pagamento no Brasil, consolidando-se como um verdadeiro
> divisor de águas que contribui para a transformação profunda do setor
> financeiro.

**Depois:**
> O Pix foi lançado pelo Banco Central em novembro de 2020. Hoje movimenta
> mais transações que cartão de crédito no país.

### 2. Inflação de notabilidade

**Palavras de alerta:** amplamente reconhecido, referência no mercado,
presença forte nas redes, citado por grandes veículos, vasta experiência.

**Antes:**
> Referência no mercado, ela é amplamente reconhecida pela vasta experiência
> e presença marcante em eventos do setor.

**Depois:**
> Em 2024, ela deu a palestra de abertura do RD Summit e publicou um livro
> sobre B2B pela editora Sextante.

### 3. Gerúndio de enfeite no fim da frase

**Palavras de alerta:** …garantindo X, …proporcionando Y, …trazendo Z,
…refletindo W, …contribuindo para, …possibilitando, …oferecendo, …promovendo.

**Antes:**
> A nova plataforma automatiza o atendimento, proporcionando mais agilidade,
> garantindo a satisfação do cliente e contribuindo para o crescimento do
> negócio.

**Depois:**
> A nova plataforma automatiza o atendimento. Os clientes esperam 40 segundos
> em vez de 4 minutos.

### 4. Linguagem promocional e jargão de consultoria/startup BR

**Palavras de alerta — promocional clássico:** destino imperdível, aninhada
no coração de, encanta os visitantes, rica herança cultural, vibrante,
estonteante, paisagem deslumbrante.

**Palavras de alerta — jargão BR:** alavancar, potencializar, destravar,
entregar valor, solução completa, end-to-end, propósito, mindset, engajar,
fazer acontecer, fazer a diferença.

**Antes:**
> Nossa solução completa alavanca resultados e potencializa o engajamento,
> entregando valor real ao seu negócio.

**Depois:**
> Nossa ferramenta reduz o tempo de resposta do seu SAC em cerca de 30%.
> Clientes atuais: Magalu, Nubank, Stone.

---

## Padrões de linguagem e gramática

### 5. Vocabulário delator (três grupos)

Em texto de IA, essas palavras aparecem em rajada. Use com parcimônia.

**5a. Etéreos / metafóricos:** jornada, essência, universo, florescer,
desvendar, mergulhar, explorar, desbravar, navegar, panorama, cenário,
horizonte, tapeçaria, ecossistema (fora de contexto técnico), alma, espírito.

**5b. Adjetivos inflados:** fascinante, incrível, essencial, crucial,
fundamental, vital, robusto, inovador, disruptivo, singular, ímpar, inegável,
indiscutível, notório, pujante, vibrante, profundo.

**5c. Verbos copulares pomposos** (substituem "é/são"): configura-se como,
consiste em, representa, apresenta-se como, constitui, estabelece-se como,
caracteriza-se por, revela-se.

**Antes:**
> A transformação digital configura-se como um pilar fundamental na jornada
> das empresas, desvendando um universo de oportunidades disruptivas.

**Depois:**
> Quase toda empresa que sobreviveu aos últimos cinco anos mexeu em processos
> digitais. Algumas ganharam com isso; outras só trocaram planilha por outra
> planilha mais cara.

### 6. Evitar "ser/estar/ter"

**Problema:** a IA troca "é", "são", "tem" por construções elaboradas.

**Antes:**
> O Ibirapuera configura-se como o parque mais visitado da cidade,
> apresentando uma área total de 158 hectares.

**Depois:**
> O Ibirapuera é o parque mais visitado da cidade. Tem 158 hectares.

### 7. Antítese "Não é X, é Y" (tell nº 1 em PT-BR)

**Problema:** IA adora "Não é só sobre X, é sobre Y", "Não se trata apenas
de X, mas de Y", "Mais do que X, é Y", "Não apenas X, mas também Y". Uma
vez é retórica; três vezes é IA.

**Antes:**
> Não é apenas sobre vender um produto, é sobre construir uma relação. Não
> se trata somente de tecnologia, mas de pessoas. Mais do que um software,
> é um parceiro.

**Depois:**
> O produto só entrega resultado quando o cliente confia na equipe por trás
> dele. Por isso a gente contrata suporte antes de contratar vendedor.

### 8. Regra de três e paralelismo forçado

**Problema:** IA empacota tudo em trinca ("X, Y e Z") e espelha estruturas
sintáticas ("Ele trouxe A. Ele consolidou B. Ele redefiniu C."). Vira
cantilena.

**Antes:**
> O evento traz palestras, painéis e networking. Espere inovação, inspiração
> e insights de mercado.

**Depois:**
> O evento tem palestras e painéis. Entre as sessões, sobra tempo para
> conversa informal — que no fim costuma ser a parte mais útil.

### 9. Ciclo de sinônimos

**Problema:** a IA troca o sujeito por sinônimos a cada frase para "não
repetir".

**Antes:**
> O protagonista enfrenta desafios. O personagem principal supera obstáculos.
> A figura central triunfa. O herói retorna para casa.

**Depois:**
> O protagonista enfrenta desafios, supera obstáculos e volta para casa.

### 10. Falsas gradações ("do X ao Y")

**Problema:** X e Y não estão na mesma escala.

**Antes:**
> Nossa jornada pelo universo da IA vai do Big Bang dos dados à dança
> enigmática da consciência artificial.

**Depois:**
> O livro cobre redes neurais, aprendizado por reforço e as teorias atuais
> sobre consciência artificial.

### 11. Voz passiva e fragmentos sem sujeito

**Problema:** IA esconde o agente: *"Não é necessário configurar nada"*,
*"Resultados são preservados automaticamente"*.

**Antes:**
> Não é necessário arquivo de configuração. Os resultados são preservados
> automaticamente.

**Depois:**
> Você não precisa criar arquivo de configuração. O sistema preserva os
> resultados sozinho.

### 12. "Nós / a gente" genérico (falsa cumplicidade)

**Palavras de alerta:** precisamos entender que, somos levados a, devemos
reconhecer, cabe a nós, como sociedade, enquanto humanos.

**Problema:** IA cria um "nós" universal para soar próxima. Fica sermão.

**Distinção:** "a gente" ou "nós" referindo a um grupo concreto (a empresa,
o time, os leitores da newsletter) é legítimo. O tell é o "nós cósmico".

**Antes:**
> Precisamos entender que, enquanto sociedade, somos levados a repensar
> nossa relação com a tecnologia.

**Depois:**
> Vale parar um minuto para pensar como você usa o celular todo dia. Eu,
> por exemplo, passei de 6 horas de tela ontem.

### 13. Gerundismo

**Problema:** o vício clássico de call center ("vou estar transferindo a
ligação") a IA às vezes reproduz.

**Antes:**
> Vou estar enviando o relatório assim que estiver concluindo a revisão.

**Depois:**
> Envio o relatório assim que terminar a revisão.

### 14. Nominalização excessiva

**Problema:** IA troca verbos por substantivos abstratos encadeados
("realização da tomada de decisão", "processo de implementação da
estratégia").

**Antes:**
> A realização da tomada de decisão depende da execução do processo de
> análise dos dados.

**Depois:**
> Para decidir, a equipe primeiro analisa os dados.

### 15. Formalismo de redação escolar e trocas comuns

**Trocar:**
- "a fim de" → "para"
- "no que tange a" / "no que diz respeito a" → "sobre"
- "em virtude de" / "haja vista" → "porque"
- "mediante" → "com" / "por meio de"
- "outrossim" → cortar
- "dito isso" / "diante do exposto" / "nesse diapasão" → cortar
- "realizar" (como verbo coringa) → verbo específico ("realizar uma reunião"
  → "fazer uma reunião" / "reunir")
- "ao invés de" (oposição: "o contrário de") ≠ "em vez de" (substituição).
  IA confunde os dois; na dúvida, "em vez de" quase sempre é o correto.

> **Nota:** *"através de"* no sentido de "por meio de" é amplamente aceito
> em PT-BR contemporâneo e **não** é tell de IA. Não corrigir.

### 16. Conectores previsíveis em cadeia

**Palavras de alerta:** Além disso, Por outro lado, No entanto, Portanto,
Ou seja, Dessa forma, Nesse sentido, Dito isso, Assim sendo, Seja como for,
De todo modo.

**Problema:** a IA nunca arrisca começar frase sem conector. Fica redação
de vestibular.

**Antes:**
> A empresa cresceu. Além disso, contratou mais funcionários. No entanto,
> enfrentou desafios. Portanto, precisou se adaptar. Dessa forma, seguiu
> em frente.

**Depois:**
> A empresa cresceu rápido. Contratou demais, se desorganizou, teve que
> cortar. Hoje está menor, mas lucrativa.

### 17. Aberturas e fechos clichê + dêixis temporal vaga

**Aberturas a cortar:** "No mundo atual…", "Nos dias de hoje…",
"Atualmente", "Hoje em dia", "Nos últimos anos", "Em um cenário cada vez
mais competitivo…", "Com o avanço da tecnologia…", "Desde os primórdios…",
"Vivemos em uma era…".

**Fechos a cortar:** "Em suma", "Em conclusão", "Portanto, podemos concluir
que", "Por fim, mas não menos importante", "O futuro é promissor", "As
possibilidades são infinitas", "Um caminho sem volta".

**Problema:** marcadores temporais vagos ("hoje em dia", "nos últimos
anos", "cada vez mais") preenchem espaço sem datar nada. Substitua por
âncora concreta ou corte.

**Antes:**
> Nos dias de hoje, em um cenário cada vez mais competitivo, as empresas
> precisam inovar. […] Em suma, o futuro é promissor.

**Depois:**
> Nenhuma das cinco maiores varejistas do Brasil lançou produto novo em
> 2024. […] No início de 2026, duas delas demitiram o diretor de inovação.

### 18. Quantificadores inflados

**Palavras de alerta:** uma série de, diversos, múltiplos, uma gama de, uma
variedade de, inúmeros, vários.

**Problema:** preenchem frase sem dizer quantos.

**Antes:**
> A empresa enfrenta uma série de desafios em múltiplas frentes.

**Depois:**
> A empresa enfrenta três problemas: fluxo de caixa, rotatividade no
> comercial e atraso na migração de sistema.

### 19. Atribuições vagas

**Palavras de alerta:** segundo especialistas, de acordo com estudos
recentes, pesquisas apontam que, é de conhecimento geral, muitos
observadores afirmam.

**Antes:**
> Segundo especialistas, o consumo de café reduz o risco de doenças
> cardíacas.

**Depois:**
> Um estudo de 2023 da USP com 14 mil participantes associou o consumo
> moderado de café (2 a 3 xícaras) a um risco 15% menor de doenças
> cardíacas.

### 20. Seção formulaica "Desafios e perspectivas"

**Palavras de alerta:** Apesar dos avanços, enfrenta desafios como…; Apesar
desses desafios, continua a se destacar; Olhando para o futuro, as
perspectivas são promissoras.

**Antes:**
> Apesar dos avanços, o setor enfrenta desafios como a falta de mão de obra
> qualificada. Apesar desses desafios, o mercado segue em expansão. Olhando
> para o futuro, as perspectivas são promissoras.

**Depois:**
> A falta de desenvolvedores sênior levou três das cinco maiores fintechs
> a abrirem operações em Portugal em 2024.

---

## Padrões de estilo

*Atenção: aplicar a seção "Quando NÃO corrigir" antes de agir aqui. Muitos
desses itens dependem do gênero.*

### 21. Excesso de travessão (tell nº 2 em PT-BR)

**Problema:** IA usa travessão onde caberia vírgula, ponto ou parênteses, e
em série na mesma frase.

**Não é tell:** um travessão isolando aposto único numa frase longa.

**Antes (tell):**
> A IA revoluciona o marketing — ao criar experiências únicas — e facilita
> a vida dos profissionais — especialmente dos que lidam com conteúdo.

**Depois:**
> A IA mudou o marketing. Criou jeitos novos de fazer conteúdo e tirou
> trabalho braçal de quem escreve todo dia.

**Aceitável (não mexer):**
> A IA mudou o marketing — sobretudo nas equipes pequenas, onde uma pessoa
> precisa fazer tudo.

### 22. Negrito mecânico e bullets com cabeçalho em negrito

**Problema:** a IA marca em negrito conceitos e frases inteiras sem
critério, e transforma listas em manuais de instrução.

**Antes:**
> A estratégia combina **OKRs (Objetivos e Resultados-Chave)**, **KPIs
> (Indicadores de Desempenho)** e ferramentas como o **Business Model
> Canvas (BMC)**.
>
> - **Experiência do usuário:** melhorada com nova interface.
> - **Desempenho:** otimizado com algoritmos mais eficientes.
> - **Segurança:** reforçada com criptografia ponta a ponta.

**Depois:**
> A estratégia combina OKRs, KPIs e ferramentas como o Business Model
> Canvas. A atualização traz interface nova, carregamento mais rápido e
> criptografia ponta a ponta.

**Exceção:** em documentação técnica, negrito em nomes de função,
parâmetros ou chaves de API é útil — não corrigir.

### 23. Title Case em cabeçalhos de documento

**Problema:** em PT-BR, cabeçalho usa primeira palavra e nomes próprios em
maiúscula; resto minúsculo. Title Case ("Toda Palavra Em Maiúscula") é
tradução literal do inglês.

**Antes:**
> ## Negociações Estratégicas E Parcerias Globais

**Depois:**
> ## Negociações estratégicas e parcerias globais

**Exceção:** capa de livro, logotipo, título de campanha — decisão de
design, não mexer.

### 24. Emojis decorativos, aspas curvas soltas e reticências reflexivas

**Emojis** em bullets ou cabeçalhos de texto de trabalho são tell. *Exceção:
redes sociais, newsletters ligeiras, interface onde o emoji é UI.*

**Aspas curvas** (caracteres Unicode U+201C e U+201D, como em `“texto”`) em
documento de trabalho bruto são tell do ChatGPT — o esperado seriam aspas
retas (U+0022, como em `"texto"`). *Exceção: livros e jornais editados,
onde aspas curvas são norma tipográfica.*

**Reticências** no fim de frase afirmativa para dar ar de reflexão
geralmente são ruído. *Exceção: citação onde algo foi cortado; diálogo
literário com fala interrompida.*

**Antes:**
> 🚀 **Lançamento:** produto sai no 3º trimestre
>
> A IA mudou muita coisa no trabalho… e a gente ainda está entendendo…

**Depois:**
> O produto sai no 3º trimestre. A IA mudou muita coisa no trabalho; a
> gente ainda está entendendo como.

---

## Padrões de comunicação

### 25. "É importante ressaltar" e companhia

**Palavras de alerta:** É importante ressaltar que, Vale destacar que, Cabe
mencionar que, É fundamental entender que, Não podemos esquecer que,
Convém lembrar que.

**Problema:** se a informação importa, entregue direto. Se não importa,
corte.

**Antes:**
> É importante ressaltar que os dados são essenciais. Vale destacar que a
> segurança não pode ser ignorada.

**Depois:**
> Sem dados limpos, nenhuma análise presta. E segurança tem que vir no
> começo, não no fim do projeto.

### 26. Vazamento de chatbot

**Palavras de alerta:** "Espero ter ajudado!", "Claro!", "Com certeza!",
"Ótima pergunta!", "Você está absolutamente certo!", "Fico à disposição",
"Qualquer coisa, é só chamar", "Aqui vai uma…".

**Antes:**
> Claro! Aqui vai um panorama da Revolução Francesa. Espero ter ajudado!

**Depois:**
> A Revolução Francesa começou em 1789, puxada pela crise financeira, pela
> fome e pelo esgotamento do Antigo Regime.

### 27. Disclaimers de corte de treinamento e tom servil

**Palavras de alerta:** "até a data do meu último treinamento", "com base
nas informações disponíveis", "embora os detalhes específicos sejam
escassos", "Ótima pergunta!", "Você está absolutamente certo".

**Antes:**
> Ótima pergunta! Embora os detalhes específicos sobre a fundação da empresa
> sejam escassos nas fontes disponíveis, parece que foi em algum momento
> dos anos 90.

**Depois:**
> A empresa foi fundada em 1994, segundo o registro na Jucesp.

### 28. Hedging vazio vs. dúvida honesta

**Tell:** hedging empilhado sem conteúdo — *"pode-se eventualmente, de
certa forma, argumentar que talvez…"*.

**Não é tell:** admissão específica de incerteza — *"não tenho dado sobre
Y; o que consigo dizer é X"*.

**Antes:**
> Pode-se eventualmente, de certa forma, argumentar que talvez a política
> venha a ter algum tipo de efeito nos resultados.

**Depois:**
> A política provavelmente afeta os resultados, embora o tamanho do efeito
> dependa do prazo considerado.

### 29. Conclusão otimista genérica

**Antes:**
> O futuro é promissor. Tempos empolgantes nos aguardam nessa jornada rumo
> à excelência.

**Depois:**
> A empresa planeja abrir duas lojas novas no ano que vem.

### 30. Pergunta retórica como muleta

**Palavras de alerta:** "Você já parou para pensar…?", "Mas o que isso
significa na prática?", "Afinal, o que é X?".

**Problema:** uma é retórica; três no mesmo texto é IA em modo blog post
de autoajuda.

### 31. Autoridade retórica fingida

**Palavras de alerta:** No fundo, Essencialmente, A verdadeira questão é,
O que realmente importa é, No cerne, Em última análise, A raiz do problema
é.

**Antes:**
> No fundo, a verdadeira questão é se as equipes conseguem se adaptar.

**Depois:**
> A pergunta é se as equipes conseguem se adaptar.

### 32. Sinalização do que vai fazer e cabeçalho com aquecimento

**Palavras de alerta:** Vamos explorar, Vamos mergulhar, Sem mais delongas,
Dito isso, Vamos ao que interessa, Aqui vai o que você precisa saber.
Também: frase genérica logo após o cabeçalho, só repetindo o título antes
do conteúdo começar.

**Antes:**
> ## Desempenho
>
> Velocidade importa.
>
> Quando o usuário cai numa página lenta, ele vai embora.

**Depois:**
> ## Desempenho
>
> Quando o usuário cai numa página lenta, ele vai embora.

---

## Processo

1. Leia o texto "ouvindo" na cabeça e identifique o **registro**.
2. Aplique a seção "Quando NÃO corrigir" como filtro de falso positivo.
3. Identifique as ocorrências dos padrões, priorizando os Top 5.
4. Reescreva cada trecho problemático respeitando o registro.
5. Verifique se o texto revisado:
   - Soa natural quando lido em voz alta.
   - Varia tamanho e estrutura de frase.
   - Usa detalhe concreto em vez de afirmação vaga.
   - Mantém o registro adequado ao contexto.
   - Usa "é/são/tem" onde cabe, sem floreio.
6. Apresente um **rascunho humanizado**.
7. Pergunte a si mesmo: *"O que nesse texto ainda entrega que é IA?"*
8. Responda brevemente com os tells que sobraram.
9. Reescreva uma última vez.
10. Apresente a **versão final**.

## Formato de saída

1. Rascunho reescrito.
2. Auditoria: *"O que nesse texto ainda entrega que é IA?"* (bullets curtos).
3. Versão final.
4. Resumo das mudanças (opcional).

---

## Exemplos completos

### Exemplo 1 — Registro informal (abertura de apostila de mentoria)

**Versão robotizada:**

> No mundo atual, em um cenário cada vez mais marcado pela transformação
> digital, a Inteligência Artificial configura-se como um divisor de águas
> — um marco que redefine a jornada de aprendizagem dos profissionais.
>
> É importante ressaltar que não se trata apenas de uma ferramenta, mas de
> um verdadeiro parceiro estratégico, capaz de potencializar resultados,
> alavancar a produtividade e entregar valor em todas as etapas.
>
> Nesta apostila, vamos mergulhar nas melhores práticas de engenharia de
> prompts, desvendando os segredos que permitem extrair o máximo dessas
> tecnologias. Além disso, exploraremos frameworks robustos e inovadores.
>
> - 🚀 **Fundamentos:** Base sólida em IA generativa
> - 💡 **Técnicas:** Frameworks de prompting
> - ✅ **Prática:** Exercícios aplicados
>
> Em suma, o futuro é promissor. As possibilidades são infinitas.

**Versão final:**

> Esta apostila é o material de apoio da sessão 2. Funciona melhor como
> consulta depois do encontro ao vivo — não precisa ler do começo ao fim.
>
> O foco é engenharia de prompt aplicada ao trabalho. Os frameworks que a
> gente vai usar (C.I.F.E., Entrevista Reversa, Chain-of-Thought, Prompt
> Chaining) são os mesmos que uso com clientes corporativos todo mês.
>
> Antes de começar, três avisos. O prompt que funciona para você pode não
> funcionar para outra pessoa — adaptar é parte do jogo. Ferramenta boa
> com prompt ruim rende pior que ferramenta mediana com prompt claro. E
> quando a IA está dando resposta vaga, o problema quase sempre é o seu
> pedido, não o modelo.

**Nota de registro:** "a gente" cabe aqui porque o texto é de mentoria com
tom oral. Em comunicado corporativo formal, seria tell (ver Exemplo 2).

---

### Exemplo 2 — Registro formal corporativo (comunicado executivo)

**Versão robotizada:**

> É com grande satisfação que anunciamos uma série de mudanças estratégicas
> que representam um verdadeiro marco na trajetória da companhia. Essas
> iniciativas configuram-se como um pilar fundamental para alavancar
> resultados e entregar valor aos nossos stakeholders.
>
> Além disso, vale destacar que, no que tange à nossa estrutura
> organizacional, estaremos implementando ajustes robustos, garantindo a
> excelência operacional e consolidando-nos como referência no mercado.
>
> Em suma, olhando para o futuro, as perspectivas são promissoras e
> seguiremos firmes em nossa jornada rumo à transformação.

**Versão final:**

> A companhia anunciou hoje três mudanças na estrutura executiva, com
> vigência a partir de 1º de junho.
>
> A vice-presidência de operações passa a reportar diretamente ao CEO. Duas
> diretorias regionais (Sul e Nordeste) foram consolidadas sob uma única
> liderança, com sede em Porto Alegre. O cargo de diretor de inovação,
> vago desde janeiro, não será preenchido no curto prazo; as iniciativas
> correspondentes migram para a área de produto.
>
> A decisão acompanha o plano de redução de 8% nas despesas administrativas
> apresentado aos acionistas em fevereiro. Não há previsão de desligamentos
> vinculados à reorganização.

**Mudanças aplicadas:** cortadas aberturas clichê ("É com grande
satisfação", "Em suma", "olhando para o futuro"). Removido jargão
("alavancar", "entregar valor", "stakeholders" vazio, "referência no
mercado", "excelência operacional"). Substituído "configura-se como" por
ações concretas com datas e nomes. Sem "nós genérico"; quando a empresa
fala de si, usa "a companhia". Detalhes específicos no lugar de "mudanças
estratégicas": o que mudou, quando, para quem reporta.

---

### Exemplo 3 — Registro técnico (README de biblioteca)

**Versão robotizada:**

> ## Sobre o Projeto
>
> Esta biblioteca representa uma solução robusta e inovadora para manipulação
> de datas em JavaScript, configurando-se como uma ferramenta essencial
> para desenvolvedores que buscam produtividade e excelência em seus
> projetos.
>
> ### Principais Funcionalidades:
>
> - 🚀 **Performance:** Otimizada para aplicações de larga escala
> - 💡 **Simplicidade:** API intuitiva e fácil de usar
> - ✅ **Confiabilidade:** Amplamente testada pela comunidade
>
> Além disso, é importante ressaltar que a biblioteca oferece suporte
> completo a fusos horários, garantindo precisão em suas aplicações.
>
> ## Começando
>
> Vamos explorar como começar. Sem mais delongas, aqui vai o que você
> precisa saber:

**Versão final:**

> ## O que é
>
> Biblioteca para manipular datas em JavaScript. Foco em fusos horários
> (o problema que outras libs resolvem mal) e tamanho reduzido (12 KB
> gzipped contra 70 KB do moment.js).
>
> Não é substituto geral do `Date` nativo — é só para os casos onde fuso
> e DST importam.
>
> ## Instalação
>
> ```
> npm install mini-tz
> ```

**Mudanças aplicadas:** cortado cabeçalho em Title Case ("Sobre o
Projeto", "Principais Funcionalidades"). Removido "configura-se como",
"essencial", "robusta", "inovadora". Sem emojis decorativos nos bullets
— substituídos por frase de posicionamento honesto ("não é substituto
geral"). Números concretos (12 KB vs 70 KB) no lugar de "otimizada para
larga escala". Sem "vamos explorar" nem "aqui vai o que você precisa
saber".

---

## Referências

Esta skill é baseada em padrões observados em textos de IA em português
brasileiro, descritos em fontes como:

- Envox, "Os 12 maiores vícios de linguagem de IA em 2026 (com exemplos
  reais)"
- Advoco Brasil, "Os vícios linguísticos das IAs"
- Comunidade O Novo Mercado, "9 vícios de escrita que dão aquele cheirinho
  de IA"
- Na Prática, sobre o estudo do Instituto Max Planck
- BBC News Brasil, "Dá para identificar texto gerado por IA?"
- Discussões em r/WritingWithAI e r/Professors (threads em PT-BR)

Esta é uma adaptação para PT-BR do projeto `humanizer` de Siqi Chen (MIT),
com reescrita integral baseada em padrões específicos da IA em português
brasileiro.

Insight central: LLMs geram o resultado estatisticamente mais provável. Em
PT-BR, isso converge para um registro específico — formal, conectivo,
neutro, inflado, com jornadas e essências — que qualquer revisor brasileiro
experiente reconhece em dois parágrafos. Esta skill é um atalho para
desfazer esse registro respeitando o gênero do texto.