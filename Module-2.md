## IA generative foundations
### Module 2: Large Language Models (LLMs)
----
#### O que aprenderemos:
-Nesse módulo, iremos aprender o básico sobre LLMs: o que eles fazem e como eles funcionam(tudo em nível técnico). 
-Técnicas de Prompt(solicitação) que são mais usadas para as LLMs gerarem textos com características específicas.
- Treinamento e codificação para gerar textos LLMs
- Perigos sobre implatação de tecnologias com LLMs
-Temas que ainda estão sendo desenvolvidos.
 ----
 #### Introdução as LLMs
 - O que exatamente são modelos LLMs? Talvez você já tenha se perguntado e não soubesse a resposta, mas iremos explicar exatamente o que são. "Language Models (LMs) são modelos probabilísticos de texto" é uma das definições, essa usada pela Oracle, mas o que exatamente significa isso? Digamos que eu tenha essa frase: "Eu pedi para minha mãe comprar uma camisa para mim,  ela disse que __", um modelo de lnguagem irá calcular a distribuição de possíveis vocabulários, ou seja, o LM conhece uma gama de palavras chamada vocabulário e escolherá a mais apropriada, mas sem usar palavras fora do seu vocabulário. O output do texto acima podendo ser: ("vai",70%);("talvez",20%);("não",10%). Claro que é apenas um exemplo, as porcentagens e as respostas dependem do treinamento e do vocabulário. 

-LLMS não são diferentes dos modelos LMs, adição de "Large" no termo corresponde o termo grande, mas se for se levar ao pé da letra, não faz sentido. O termo grande se refere ao número de parâmetros no modelo, mas não existe um fronteira acordada para definir a quantidade de parâmetros necessários para considerar um modelo grande ou pequenos, mas é comum usar ele quando a quantidade de parâmetros é extremamente maior. 

-LLMs, como já sabemos, podem fazer a distribuição de possíveis outputs de vocabulário, mas podemos afetar essa distribuição de respostas? A resposta é sim, para mudarmos a distribuição existem certos mecanismos, mas que aprenderemos mais tarde.

#### Arquitetura de LLMs
- Vamos nos concetrar em duas principais arquiteturas: codificadores e decodificadores. Tais arquiteturas correspondem a duas tarefas diferentes.
<br>
  1. Codificadores: esse corresponde a incorporação, seu papel é ler e compreender o texto, gerando uma representação densa e compacta. Essa arquitetura é mais recomendada para classificação de textos e análise de textos
  2. Decodificadores: esse corresponde a geração de texto. Eles pegam uma representação de texto, que pode ter vindo do codificador ou de outro contexto, com isso, geram uma sequência de palavras.
<br>
  Ambos esses modelos são construídos em um bloco de construção chamado transformador, que foi popularizado no artigo "Attention is All You Need", de 2017. Esse modelo revolucionouo processamento de NLP e ML em geral ,ele é bem eficiente, pois é capaz de processar sequência de textos de forma mais eficiente e paralela. Ao falar que estamos incorporando texto, estamos nos referindo ao processo de conversão de uma sequência de palavras em um único vetor ou uma sequência de vetores.
  <br>

      | Modelo             | Tipo              | Parâmetros         |
      |--------------------|-------------------|--------------------|
      | BERT/roBERTa       | Encoder            | 110M-1B            |
      | DistilBERT         | Encoder            | 100M               |
      | GPT-3              | Decoder            | 100B-1T            |
      | GPT-4              | Decoder            | 1T                 |
      | BART               | Encoder-Decoder    | 1B-10B            |
      | FLAN-T5            | Encoder-Decoder    | 11B                |
      Fonte: Oracle


<br>
  A tabela acima dá uma ideia de quantos são os parâmetros treináveis, alguns modelos tem. Encoder-Decoder é uma mistura da arquitetura encoder com decoder, nada muito fora da expectativa. Existe algo interessante de notar, que os modelos encodificadores são tendem a ser maiores que os modelos codificadores. O motivo deles serem maiores é porque não há motivo para os codificadores seram muit grandes, pois eles não precisam ter uma gama de possíveis saídas e contexto da situação, como são os decodificadores, codificadores são mais focados em transformar informações de forma eficiente e compactas. Se o mesmo fosse feito para decodificadores, o output seria de baixa qualidade. Apesar de tudo que foi tido, pesquisa mais recentes podem ter detectado esse padrão mudando, já que foram capazes de gerar resposta fluentes  com modelos pequenos.
  <br>

  #### Tokens

  -Tokens são as menores unidades que um modelo decodificador pode usar. Ele pode ser uma palavra, sílabas ou até mesmo caracteres, depende muito da forma que é utilizado.
  Digamos que você coloque em um modelo: "Eu quero jogar videogame", a frase será transformada em uma lista de tokens, depois cada token é mapeado para um vetor (embedding), que mostra o token e seu significado em relações aos outros tokens. O modelo manipula esses embeddings durante a geração de suas respostas, suas predições ou sua tradução. É importante saber que decodificadores geram apenas um token por vez! Não ocorre de forma paralela

  #### Encoders-Decoders

  São feitos exatamente com sooam, uma mistura de ambos os modelos, uma junção dos dois modelos. São principalmente usados em tarefas de sequência a sequência. Funciona da seguinte forma: os tokens são enviados ao modelo, que são passados ao codificador, que incorpora todos os tokens, então as incorporações são passadas ao decodificador, que decodifica as palavras(uma por vez). Durante o processo, há loops de autorreferência para o decodificador, mas isso apenas representa a geração de tokens uma por vez, como foi discutido. Após gerar o token, ele é passado de volta para o decodificador, junto com a sequência de tokens já gerados para construir a próxima palavra, que novamente irá virar um token e ser repassada para o decodificador, isso até não restarem mais tokens para serem gerados.

  <br>

  #### Prompting 

  -Nesta seção, irá se discutir sobre prompts.

  -Para ilustrar, um exemplo passado será usado: "Eu pedi para minha mãe comprar uma camisa para mim,  ela disse que __". Como dito, os LLMs calculam a distribuição encima da próxima palavra e escolhem a mais adequada. O que será aprendido é como exercer controle sobre a distribuição da próxima palavra, atualizando as probabilidades ou afetando-as. Há duas principais formas de ocasionar isso: estímulo e treinamento.
    A maneira mais simples de alterar a probabilidade das palavras é por meio de prompt. Durante os estudos, é comum ouvir a palavra prompt no uso de LLMs. O termo possui mais de um significado, mas a forma mais simples de entender o prompt é que ele se refere a altereção do conteúdo ou a estrutura da entrada que você está usando ao modelo. Apesar de poder ser óbvio, é importante citar que com a alteração da entrada de texto, consequentemente, haverá mudanças posteriores na distribuição de probabilidades do vocabulário. Digamos que no exemplo usado no início da seção, colocássemos a palavra vermelha após camisa, o vocabulário iria tender a ter uma distribuição diferente, mesmo que a diferença provavelmente seja pequena nesse caso. Talvez você se pergunte o motivo das LLMs conseguirem fazer isso, isso se deve porque modelos decodificadores muito grandes possuem um treinamento prévio, um procedimento chamado pré-treinamento, durante esse processo, um modelo recebe uma enorma quantidade de informação com os temas dos textos sendo variados. Com isso, o modelo é treinado para adivinhar o próximo passo, ou seja, a próxima palavra provável e o quais são as chances de ser essa palavra.
    <br>

  #### Prompt Engineering

  -Esse é o processo de refinar nosso prompt, de forma que o resultado seja o melhor possível para o caso desejado, ou seja, ocorre uma indução para que a distribuição de probabilidade seja um de interesse do usuário. Normalmente, isso é feito alterando a entrada do modelo até ter uma satisfatória. Quando se está a realizar tal processo, a distribuição do vocabulário não está necessariamente sendo observada. No geral, geramos a entrada e vemos se o texto gerado está bom ou não.
  <br>
  -Prompt Engineering nem sempre é intuitivo, pode ser bastante desafiador. Ao realizar uma pequena mudança na entrada, por exemplo, colocar um letra errada ou um espaço sem necessidade, pode gerar um grande efeito no output e não se sabe qual mudança ocorrerá. Entretanto, apesar da existência de desafios, estão surgindo muito estratégias e design de prompts que tem se provado bastante efetivo. Assim, gastar um tempo para achar o prompt ideal pode ser extremamente recompesador. Será apresentado algumas das principais estratégias de prompt:
  <br>
  1-*In the context learning*: nenhum dos parâmetros do modelo está mudando, mas a construção do prompt com um exemplo da tarefa que o modelo precisa concluir

  2-*k-shot prompting*: incluir k exemplos da tarefa que o modelo deve concluir.
  <br>

  - Incluir k exemplos antes do prompt(nesse caso, se refere ao comando), consegue melhores resultados do que não incluir nenhum exemplo ou demonstração. O ato de não incluir nenhum exemplo se chama 0-shot prompting.

  #### Advanced Prompting Strategies

  1-*Chain-of-thought*:Desenvolvido em 2022, ainda é bastante popular, funciona da seguinte forma: se houver uma tarefa complicada de ser finalizada, a ideia é quebrar o problema complexo em pequenas partes, partes que , de forma unitária, não são tão complexas. Quando damos uma perguna ao modelo, ele está apenas a gerar palavras de cada vez, ele não possui um grande plano de como resolver o problema, apenas gerando uma palavra por vez. Há duas hipóteses para o funcinamento: a primeira é que os dados de pré-treinamento exite problemas que são divididos em partes e são resolvidos. A segunda hipótese é que quando dividimos o problema em partes, os subproblemas são algo que o modelo consiga resolver. Se dermos, inteiramente, um problema muito complexo para o modelo, talvez ele não consiga solucionar.
  
  2-*Least-to-Most*: ??? 

  3-*Step-back*: possui um grande desempenho em questões de quimíca. Os criadores descobriram que se antes da pergunta, colocar os conceitos e os princípios e equações necessárias para resolver o problema, o modelo consegue um bom resultado.