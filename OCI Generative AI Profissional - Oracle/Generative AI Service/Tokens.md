LMs não tem como base caracteres, mas sim tokens. Um token pode ser parte de uma palavra, uma palavra inteira ou um sinal de pontuação.

- Exemplo de token: Apple
- Exemplo de palavra composta de tokens: friendship (”friend” e “ship”)

O número de tokens por palavra depende da complexidade do texto:

- Texto simples: média de 1 token/palavra;
- Texto complexo (costuma ter palavras menos comuns): média de 2-3 tokens/palavra.

## Parâmetros de escolha de tokens:

- Maximum Output Tokens: valor máximo de tokens gerado no output do modelo.
- Temperature (já apresentado em outra anotação, [[Prompting and Prompting Engineering]] )
- Top k, Top p
- Stop Sequences
- Presence/Frequency Penalty
- Show Likelihoods

### Top k

Parâmetro que faz com que o modelo escolha o próximo token da lista de “k” tokens com maiores probabilidades.

### Top p

Parâmetro que escolha os tokens cuja soma das probabilidades seja menor ou igual ao valor de p.

### Stop Sequences

Uma string que sinaliza para o modelo quando ele deve parar de gerar o output. É uma forma de controlar a saída do modelo. Essa string encerra a saída, mesmo que não tenha atingido o limite de tokens de saída.

### Presence/Frequency Penalty

Um parâmetro que serve para tornar o output do modelo menos repetitivo. Qualquer token que tenha aparecido um determinado número de vezes, seja na saída do modelo ou no prompt, recebe uma penalidade na sua probabilidade de ser escolhido.

### Show Likelihoods

Toda vez que um token é gerado, um valor entre -15 e 0 é atribuído a todos os outros tokens. Tokens com maior valor tendem a ser gerados a partir do token atual.