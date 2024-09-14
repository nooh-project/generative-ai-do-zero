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