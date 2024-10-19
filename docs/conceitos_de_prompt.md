# Afinal, o que é um prompt?

Um prompt é todo o input fornecido a um modelo generativo que produz o resultado desejado. Esse input pode ser um texto de solicitação, uma série de perguntas entre outros.

Para elaborar um promp que o modelo consiga compreender bem, pode-se utilizar o seguinte modelo:

- Instructions
- Context
- Input data
- Output indicator 

Para os seguintes exemplos, elaborados pelo autor, foi utilizado o modelo do llama3.1 de 8 B de parâmetros da Meta, usando o projeto ollama.

## Instructions

Criar instruções claras sobre a tarefa.

Ex: Escreva um texto de 300 palavras sobre o efeito do aquecimento global na vida marinha.

![exemplo_1](./Images/Pasted%20image%2020241011091226.png)

## Context: 

Informar um contexto, para que o modelo consiga gerar a resposta alinhada com o contexto.

Ex: Recentemente, o aquecimento global passou por mudanças significativas, levando ao aumento do nível do mar, tempestades mais intensas, e mudanças nos padrões climáticos. Essas mudanças levaram a impactos sérios na vida marinha. Escreva um texto de 300 palavras sobre o efeito do aquecimento global na vida marinha.

![exemplo_2](./Images/Pasted%20image%2020241011092609.png)

## Input data: 

Qualquer tipo de informação provida como parte do prompt.

Ex: Lhe foi fornecido um conjunto de dados das medidas de temperatura no nível do mar do Oceano Pacífico. Escreva um texto de 300 palavras analizando o efeito do aquecimento global na vida marinha do oceano pacífico.

![exemplo_3](./Images/Pasted%20image%2020241011101918.png)

## Output Indicator: 

Oferecer métricas para avaliar as características do prompt.

Ex: O texto gerado deve ser de 300 palavras. Vai ser avaliado com base na clareza da análise e incorporação de dados relevantes ou estudos de caso.

![exemplo_3](./Images/Pasted%20image%2020241011102734.png)


