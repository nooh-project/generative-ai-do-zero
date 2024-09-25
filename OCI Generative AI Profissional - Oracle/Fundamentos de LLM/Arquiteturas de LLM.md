# Tipos de Arquiteturas
- Encoders
- Decoders

Ambas arquiteturas são elaboradas em cima da arquitetura de Transformer.
O tamanho de um modelo de LM se refere a quantidade de parâmetros que o modelo tem.
## Encoders

Os encoders focam em incorporar as relações e contextos dentro de um determinado texto, transformando o texto (sequência de palavras) em um vetor.

Os encoders possuem, historicamente, um menor numero de parâmetros, os que combinam encoders e decoders (encoder-decoder) possuem um valor mediano e os decoders são os maiores.

Os encoders são menores, visto que já se percebeu que aumentar a quantidade de parâmetros dele não leva uma uma melhor performance do modelo, diferentemente dos decoders que quando são muito pequenos não são bons geradores de texto. Apesar de que, segundo o curso da Oracle, esse padrão está mudando e com algumas modificações é possível gerar bons decoders com modelos pequenos.

## Decoders

Modelos que recebem como input uma sequência de palavras e tem como saída, tendo como referência a probabilidade das palavras em seu vocabulário, uma nova palavra. Um decoder emite apenas um token (palavra) por vez, para gerar um sequência de tokens (um texto) é necessário retroalimentar o decoder com o output anterior, para que assim ele vá gerando um texto com os tokens mais prováveis.

## Econder-Decoder

Basicamente a combinação de um encoder onde o output dele é o input de um decoder. Costumam ser usados para tarefas sequenciais, como tradução.
