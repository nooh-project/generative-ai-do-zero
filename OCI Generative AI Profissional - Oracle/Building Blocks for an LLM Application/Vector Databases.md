São databases otimizados para espaços multidimensionais, baseados nas distâncias e similaridades em um espaço vetorial de muitas dimensões.

Existem duas formas de se calcular a distância entre dois vetores nesse tipo de situação:

![[Pasted image 20240723092558.png]] 

Para encontrar vetores similares ou busca semântica, já foi usado o algoritmo K-Nearest Neighbors como método de busca em um espaço incorporado. Porém por ser muito custoso computacionalmente, ou seja lento, assim como em termos de memória utilizada atualmente é utilizado o algoritmo ANN (Approximate Nearest Neighbors) para achar os vetores que são mais similares visto que apesar da perda e precisão, eles são bem mais rápidos.

### Fluxo de um vector database

![[Pasted image 20240723092719.png]] 

### Mas afinal, por que usar esses databases no lugar dos mais tradicionais?

A resposta, com alguns exemplos de vector databases estão na seguinte imagem:

![[Pasted image 20240723092739.png]]

### Funções de um vector database em conjunto com LLMs

- Evitar o problema das alucinações;
- Melhorar a qualidade do output com respostas melhores;
- Evitar exceder o limite de tokens da resposta do LMM, fazendo uso do conteúdo mais relevante;
- Mais em conta que o tradicional treinamento de LLMs (que envolve o fine-tuning);
- Base de conhecimento atualizada em tempo real;
- Armazenar em Cache as respostas geradas pelo LLM para melhorar a performance e reduzir custos.