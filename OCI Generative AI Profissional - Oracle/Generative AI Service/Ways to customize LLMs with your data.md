Existem algumas formas de se treinar um LLM com seus dados, sem ter que fazer isso do zero. Até o momento, existem 3 principais formas:

1. Prompt Engineering
2. Fine-Tuning
3. Retrieval-Augmented Generation

## Prompt Engineering

Já apresentada antes nestas anotações, é uma forma de delimitar como o output do LLM deve ser gerado com instruções e/ou exemplos, isso pode ser realizado via métodos como In-Context Learning, K-shot prompting e Chain of Thought. A principal limitação disso é a capacidade de input do LLM.

## Fine-Tuning

Recomendado para quando uma determinada tarefa realizada pelo modelo não tem uma boa performance, ou quando se tem a necessidade de que o modelo aprenda a realizar algo novo ou quando se quer que ele adote um determinado estilo ou tom no output para que atenda a alguma preferência humana.

Tem como vantagem melhorar a performance do modelo em tarefas específicas, assim como a eficiência dele como um todo.

## Retrieval-Augmented Generation (RAG)

Tornar o modelo capaz de fundamentar suas respostas em fontes de informação confiáveis. Uma vantagem é de não precisar de um modelo customizado (um modelo customizado é um modelo criado usando um que já foi treinado como base, e que você personalizou com seu próprio dataset) para esse tipo de treinamento.

### Tabela resumindo estas anotações:
![[Pasted image 20240723091940.png]]
### Uma ajudinha para saber qual usar, de acordo com a necessidade

![[Pasted image 20240723092022.png]]