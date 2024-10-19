# Algumas técnicas e abordagens em prompt engineering para text-to-text prompts

## Task specification

Fazer prompts textuais que explicitem o que o LLM deve fazer.

Ex:

Sem task specification:

![exemplo_1](./Images/Pasted%20image%2020241016210805.png)

Com task specification:

![exemplo_2](./Images/Pasted%20image%2020241016210915.png)


## Contextual guidance

Fornecer instruções claras pro modelo.

Ex:

Antes:

![exemplo_3](./Images/Pasted%20image%2020241016212423.png)

Depois:

![exemplo_4](./Images/Pasted%20image%2020241016212639.png)

## Domain expertise

Usar terminologias específicas, para levar o modelo a gerar resultados precisos e exatos.

Ex:

![exemplo_5](./Images/Pasted%20image%2020241016213632.png)

## Bias mitigation

Prover instruções explicitas para que o modelo gere respostas neutras.

Ex:

![exemplo_6](./Images/Pasted%20image%2020241016214843.png)

## Framing 


Guiar o LLM para que a resposta esteja dentro de determinados limites.

Ex:

![exemplo_7](./Images/Pasted%20image%2020241016221214.png)
![exemplo_8](./Images/Pasted%20image%2020241016221229.png)

## User feedback loop

Melhorar a resposta que o modelo fornece, refinando-a com os feedbacks de um usuário.

Ex:

![exemplo_9](./Images/Pasted%20image%2020241016222558.png)

![exemplo_10](./Images/Pasted%20image%2020241016222848.png)

![exemplo_11](./Images/Pasted%20image%2020241016224338.png)

## Few-shot prompting

Dar alguns exemplos, para que o modelo possa ajustar a resposta ao que for solicitado.

# Interview Pattern Approach

Criar uma espécie de roleplay, fazendo com que o modelo assuma uma persona que irá me entrevistar.

# Chain-of-Thought Approach

Abordagem onde, no prompt fornecido ao modelo é dada um problema, uma solução para ele, e em seguida um novo problema para que o modelo entenda como ele deve abordar esse tipo de questão.

# Tree-of-Thought Approach

Uma técnica baseada na abordagem de chain-of-thought. Envolve estruturar o prompt, de modo que além de guiar a forma como a máquina aborda o problema e a geração do output.