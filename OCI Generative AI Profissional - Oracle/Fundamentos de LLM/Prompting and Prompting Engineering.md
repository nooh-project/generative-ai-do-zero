Basicamente, isso serve para influenciar o LLM, afetando a probabilidade sobre o vocabulário dele de duas formas:

- Prompting
- Training

## Prompt

O prompt se refere a uma forma de estruturar o input para um LLM, de modo que influencie na estruturação da respostas, como quando o input tem instruções ou exemplos de como o output deveria ser.

## Prompt Engineering

É basicamente o processo de formular os prompts, para melhorar as respostas dos LLMs. No entanto, não é algo intuitivo nem garante melhoria nas respostas dos modelos contudo pode ser eficiente se fizer uso de algumas estratégias.

Algumas estratégias utilizadas:

- In-context learning: Demonstrar ou instruir o modelo sobre como a resposta deve ser gerada.
- k-shot prompting : explicitamente mostrar exemplos da tarefa que deverá ser realizada, onde k é o número de exemplos fornecidos.
- Chain-of-Thought: fazer um prompt que leve o modelo a dividir a resolução do problema em etapas.
- Least-to-most: criar um prompt para o modelo que decomponha o problema em problemas menores, começando pelo caso mais simples.
- Step-Back: gerar um prompt que o modelo identifique os conceitos de alto nível que são necessários para resolver a tarefa.

## Problemas relacionados ao Prompting

- Prompting injection (jailbreaking): gerar um prompt para o modelo, que leve ele a ignorar as instruções que recebeu do desenvolvedor, causar algum tipo de dano, ou se comportar de maneiras inesperadas.