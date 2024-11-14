# Melhorando as saídas do modelo com Prompt Engineering

No último módulo, vimos como fazer certos ajustes em um modelo LLM. Um deles foi o uso de prompt para "guiar" o modelo a elaborar a resposta de que precisamos. Contudo, é possível melhorar ainda mais essa forma orientação mais eficiente.

## Prompt Engineering

É basicamente o processo de formular os prompts, para aprimorar as respostas dos LLMs. No entanto, não é algo intuitivo nem garante melhoria nas respostas dos modelos. Contudo pode ser eficiente se fizer uso de algumas estratégias específicas.

Essas são algumas das estratégias que ajudam elaborar um promp de maior qualidade.

- **In-context learning**: Demonstrar ou instruir o modelo sobre como a resposta deve ser gerada.
- **k-shot prompting**: mostrar exemplos específicos da tarefa que o modelo deverá realizar.
- **Chain-of-Thought**: fazer um prompt que leve o modelo a dividir a resolução do problema em etapas.
- **Least-to-most**: criar um prompt para o modelo que decomponha o problema em problemas menores, começando pelo caso mais simples.
- **Step-Back**: gerar um prompt que o modelo identifique os conceitos de alto nível que são necessários para resolver a tarefa.

## Problemas relacionados ao Prompting

Prompting injection (jailbreaking): gerar um prompt para o modelo, que leve ele a ignorar as instruções que recebeu do desenvolvedor, causar algum tipo de dano, ou se comportar de maneiras inesperadas. 

Apesar do problema existir, ainda não existe um consenso sobre uma maneira efetiva de lidar com este problema.