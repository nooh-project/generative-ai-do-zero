# O que é um large language model(LLM)?

"Language Models (LMs) são modelos probabilísticos de texto", uma definição desse termos, **mas o que isso significa**? Vamos a um exemplo para esclarecer isto:

Digamos que eu tenha essa frase: 
- "Eu pedi para minha mãe comprar uma camisa para mim,  ela disse que __" 

Com base nos dados que recebeu para treinamento (a forma como o modelo "aprende"), ele irá verificar quais palavras de seu repertório costumam ser mais comuns ao se ter sentenças parecidas com a que usamos de exemplo. 
Isso significa dizer que o output do texto acima poderia ser: ("vai",70%);("talvez",20%);("não",10%). Claro que dentro do nosso exemplo a portecagem de cada palavra foi definina arbitrariamente por razões didática. Nesse sentido, as porcentagens e as respostas dependem do treinamento e do vocabulário e variam tanto pelo recbimento de novos dados quanto por novos treinamentos realizados.

## e o que isso tem haver com os LLMs?

A diferença entre um modelo LM e um modelo LLM está relacionada a **quantidade de parâmetros que foram utilizadas no treinamento do modelo**, apesar de que não existe um consenso sobre qual o valor quantitavo que torna um modelo um LLM. Portanto, entende-se que a diferença se resume da seguinte forma: um LM recebeu uma quantidade x de parâmetros, enquanto que um LLM recebeu um valor de 5000 maior que x.

Aos que se perguntarem sobre *é possível influenciar os valores probabilísticos das palavras depois que o modelo é treinado?*, saiba que sim, porém isso é um assunto que será visto em outros módulos.

Por enquanto, vamos focar em entender mais como LLMs funcionam. Primeiro, conhecamos os Tokens e os embeddings:

### Embedding

- Embeddings são representações numéricas de um trecho de texto, convertido em uma sequência de números. Tal texto pode ser uma palavra, frase, sentença, parágrafo ou mais de um parágrafo. Isso facilita para o computador entender as relações entres os trechos de texto.
- Embeddings de palavras também são capazes de capturar propriedades delas, e com os métodos certos computar a similaridade numérica dessas palavras. Embeddings que são numericamente similares também o são semanticamente.
- Quando se faz embeddings de sentenças, cada uma é associada com um vetor de números, de forma que sentenças similares possuem vetores similares, e sentenças diferentes tem vetores diferentes.

### Tokens

LLMs não tem como base caracteres, mas sim tokens. Um token pode ser parte de uma palavra, uma palavra inteira ou um sinal de pontuação.

- Exemplo de token: Apple
- Exemplo de palavra composta de tokens: friendship (”friend” e “ship”)

O número de tokens por palavra depende da complexidade do texto:

- Texto simples: média de 1 token/palavra;
- Texto complexo (costuma ter palavras menos comuns): média de 2-3 tokens/palavra.

#### Parâmetros de escolha de tokens:

- Maximum Output Tokens: valor máximo de tokens gerado no output do modelo.
- Temperature (já apresentado em outra anotação, [[Prompting and Prompting Engineering]] )
- Top k, Top p
- Stop Sequences
- Presence/Frequency Penalty
- Show Likelihoods

##### Top k

Parâmetro que faz com que o modelo escolha o próximo token da lista de “k” tokens com maiores probabilidades.

##### Top p

Parâmetro que escolha os tokens cuja soma das probabilidades seja menor ou igual ao valor de p.

##### Stop Sequences

Uma string que sinaliza para o modelo quando ele deve parar de gerar o output. É uma forma de controlar a saída do modelo. Essa string encerra a saída, mesmo que não tenha atingido o limite de tokens de saída.

##### Presence/Frequency Penalty

Um parâmetro que serve para tornar o output do modelo menos repetitivo. Qualquer token que tenha aparecido um determinado número de vezes, seja na saída do modelo ou no prompt, recebe uma penalidade na sua probabilidade de ser escolhido.

##### Show Likelihoods

Toda vez que um token é gerado, um valor entre -15 e 0 é atribuído a todos os outros tokens. Tokens com maior valor tendem a ser gerados a partir do token atual.

# Arquiteturas de LLM

## Tipos de Arquitetura

Neste material vamos nos concetrar em duas principais arquiteturas: encoders e decoders.

### Encoders

Os encoders focam em incorporar as relações e contextos dentro de um determinado texto, transformando o texto (sequência de palavras) em um vetor.

Os encoders possuem, historicamente, um menor numero de parâmetros, os que combinam encoders e decoders (encoder-decoder) possuem um valor mediano e os decoders são os maiores.

Os encoders são menores que as outras possíveis combinações, pois se percebeu que aumentar a quantidade de parâmetros dele não leva uma uma melhor performance do modelo, diferentemente dos decoders que quando são muito pequenos não são bons geradores de texto. Apesar de que, segundo o curso da Oracle sobre IA generativa, esse padrão está mudando e com algumas modificações é possível gerar bons decoders com modelos pequenos.

Essa arquitetura é mais recomendada para classificação e análise de textos.

### Decoders

Modelos que recebem como input uma sequência de palavras e tem como saída, tendo como referência a probabilidade das palavras em seu vocabulário, uma nova palavra. Um decoder emite apenas um token (palavra) por vez, para gerar um sequência de tokens (um texto) é necessário retroalimentar o decoder com o output anterior, para que assim ele vá gerando um texto com os tokens mais prováveis.

De forma simples, é possível afirmar que os decoders visam gerar texts. Eles pegam uma representação de texto, que pode ter vindo do codificador ou de outro contexto, e com isso, geram uma sequência de palavras.

Tanto os encoders quanto os decoders são construídos em um bloco de construção chamado transformador, que foi popularizado no artigo "Attention is All You Need", de 2017. 

### Enconder-Decoder

Basicamente a combinação de um encoder onde o output dele é o input de um decoder. Costumam ser usados para tarefas sequenciais, como tradução.

# Conteúdos extras:

Existem algumas formas de decoding:

- Greedy Decoding: Escolher a palavra com maior probabilidade a cada passo;
- Non-Deterministic Decoding: Escolher randomicamente as palavras com maiores probabilidades em cada passo.
- Temperature: Um (hiper) parâmetro que modula a distribuição das probabilidades do vocabulário do modelo. Quando a temperatura diminui, a distribuição de probabilidades se concentram nas palavras que normalmente já são mais prováveis, contudo se ela aumenta as palavras ficam com probabilidades com valores mais próximos umas das outras. Observação: Esse parâmetro afeta as probabilidade já existentes, logo palavras mais prováveis de serem escolhidas tendem a ainda se comportarem dessa forma, assim como com as palavras menos prováveis.
