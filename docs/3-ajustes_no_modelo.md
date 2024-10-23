# Ajustando um modelo

É comum que vez ou outra, o modelo não gere a resposta que desejamos. Isso pode ocorrer devido a um ou mais dos seguintes fatores:

- Soliticação mal formulada.
- Está fora do que domíno do modelo, ou seja, fora da área na qual ele foi treinado.
- Hallucination

Existem algumas formas de lidar com essas situações:

- Prompt Engineering
- Training
- Groundedness and Attributability

## Mas, o que é um prompt?

Um prompt é todo o input fornecido a um modelo generativo que produz o resultado desejado. Esse input pode ser um texto de solicitação, uma série de perguntas entre outros. Ele consegue ter esse efeito pois é capaz de **influenciar a probabilidade sobre o vocabulário do modelo**.

## Como elaborar um bom prompt:

Para elaborar um promp que o modelo consiga compreender bem, pode-se utilizar o seguinte modelo:

- Instructions
- Context
- Input data
- Output indicator 

Para os seguintes exemplos, elaborados pelo autor, foi utilizado o modelo do llama3.1 de 8 B de parâmetros da Meta, usando o projeto ollama.

### Instructions

Criar instruções **claras** sobre a tarefa.

Ex: Escreva um texto de 300 palavras sobre o efeito do aquecimento global na vida marinha.

Saída:

```
O aquecimento global está tendo um impacto significativo na vida marinha. O aumento da temperatura das águas pode afetar a distribuição e o comportamento de muitas espécies marinhas, desde peixes até corais. A mudança nos padrões de temperatura também pode levar à perda de habitats e à alteração nos padrões de reprodução.

Além disso, o aquecimento global está causando a acidificação do oceano, que é um dos principais desafios enfrentados pelas áreas marinhas. A absorção excessiva de CO2 pelo oceano está levando à formação de ácido cítrico e à dissolução dos carbonatos essenciais para a estrutura dos corais e de muitas outras espécies marinhas.

A vida marinha também é afetada pelas mudanças nos padrões de circulação oceânica, que podem levar a uma redução na produtividade das áreas marinhas. A perda de nutrientes e oxigênio pode ter consequências graves para as populações marinhas.

O aquecimento global também está aumentando a frequência e intensidade dos eventos climáticos extremos, como furacões e ondas ciclônicas, que podem causar danos significativos às áreas marinhas. A perda de habitats e a alteração nos padrões de reprodução podem ter consequências indiretas para a humanidade, pois o oceano é uma fonte importante de alimento e recursos naturais.

É fundamental que sejam tomadas medidas imediatas para combater os impactos do aquecimento global na vida marinha. A transição energética para fontes renováveis, como energia solar e eólica, e a implementação de políticas climáticas eficazes são essenciais para reduzir as emissões de gases de efeito estufa e proteger os ecossistemas marinhos.

A vida marinha é um recurso vital para a humanidade, e sua proteção é essencial para garantir o bem-estar do planeta. É hora de agir para preservar os ecossistemas marinhos e evitar as consequências graves que podem surgir se nada for feito nada."
```

### Context: 

Informar um contexto, para que o modelo consiga gerar a resposta alinhada com o contexto.

Ex: Recentemente, o aquecimento global passou por mudanças significativas, levando ao aumento do nível do mar, tempestades mais intensas, e mudanças nos padrões climáticos. Essas mudanças levaram a impactos sérios na vida marinha. Escreva um texto de 300 palavras sobre o efeito do aquecimento global na vida marinha.

Saída:
```
O aquecimento global está tendo um impacto devastador na vida marinha. As mudanças climáticas recentes têm levado a um aumento significativo no nível do mar, causando inundação de habitats marinhos e perda de biodiversidade. Além disso, as tempestades mais intensas estão afetando as áreas costeiras, causando danos à vida marinha e às infraestruturas humanas.

As mudanças nos padrões climáticos também estão afetando a distribuição e o comportamento das espécies marinhas. Muitas espécies que dependem de condições climáticas específicas para sobreviver estão sendo deslocadas ou extintas. Isso tem consequências graves para as cadeias alimentares marinhas, pois muitos peixes e outras espécies dependem das espécies que são afetadas.

A acidificação do oceano é outro efeito devastador do aquecimento global na vida marinha. A absorção excessiva de CO2 pelo oceano está levando à formação de ácido cítrico, que dissolvia os carbonatos essenciais para a estrutura dos corais e de muitas outras espécies marinhas.

As consequências dessas mudanças são graves e afetam não apenas as áreas marinhas, mas também a humanidade. A perda de biodiversidade marinha pode ter implicações econômicas e sociais significativas, pois o oceano é uma fonte importante de alimento e recursos naturais.

É fundamental que sejam tomadas medidas imediatas para combater os impactos do aquecimento global na vida marinha. A transição energética para fontes renováveis, como energia solar e eólica, e a implementação de políticas climáticas eficazes são essenciais para reduzir as emissões de gases de efeito estufa e proteger os ecossistemas marinhos. A vida marinha é um recurso vital para a humanidade, e sua proteção é essencial para garantir o bem-estar do planeta.
```

### Input data: 

Qualquer tipo de informação provida como parte do prompt.

Ex: Lhe foi fornecido um conjunto de dados das medidas de temperatura no nível do mar do Oceano Pacífico. Escreva um texto de 300 palavras analizando o efeito do aquecimento global na vida marinha do oceano pacífico.

Saída:
```
O conjunto de dados fornecido revela uma tendência clara de aumento nas medidas de temperatura no nível do mar do Oceano Pacífico ao longo dos últimos anos. Essa elevação na temperatura é um sinal inequívoco do aquecimento global e seus impactos devastadores sobre a vida marinha.

Analisando os dados, observamos que as temperaturas mais altas estão ocorrendo em áreas de baixas profundidades, onde as espécies marinhas são mais vulneráveis às mudanças climáticas. Isso sugere que essas espécies estão sendo afetadas diretamente pelo aumento da temperatura e pelas consequências associadas, como a acidificação do oceano.

A distribuição das temperaturas também revela padrões interessantes. Áreas com correntes marinhas mais intensas estão apresentando variações mais significativas em relação às médias históricas. Isso pode ser atribuído à alteração nos padrões de circulação oceânica, que está afetando a distribuição de nutrientes e oxigênio essenciais para as espécies marinhas.

Aumentos nas temperaturas também estão associados a mudanças nos padrões de reprodução e distribuição de espécies. Peixes e outros organismos estão sendo deslocados ou extintos em áreas onde as condições climáticas não atendem às suas necessidades. Isso tem implicações graves para as cadeias alimentares marinhas e para a saúde dos ecossistemas marinhos.

Os dados fornecidos também sugerem que o aumento da temperatura está afetando a produtividade das áreas marinhas. A redução na abundância de nutrientes e oxigênio está comprometendo a capacidade dessas áreas de sustentar vida marinha.

Em resumo, os dados sobre as medidas de temperatura no nível do mar do Oceano Pacífico revelam um quadro sombrio para a vida marinha. As consequências do aquecimento global estão sendo sentidas em todo o ecossistema, e é fundamental que sejam tomadas medidas imediatas para proteger esses recursos vitais para a humanidade.
```

### Output Indicator: 

Oferecer métricas para avaliar as características do prompt.

Ex: O texto gerado deve ser de 300 palavras. Vai ser avaliado com base na clareza da análise e incorporação de dados relevantes ou estudos de caso.

Saída:
```
O conjunto de dados fornecido sobre as medidas de temperatura no nível do mar do Oceano Pacífico revela uma tendência clara de aumento nas temperaturas ao longo dos últimos anos. Esse aumento é um sinal inequívoco do aquecimento global e seus impactos devastadores sobre a vida marinha.

Analisando os dados, observamos que as temperaturas mais altas estão ocorrendo em áreas de baixas profundidades, onde as espécies marinhas são mais vulneráveis às mudanças climáticas. Isso sugere que essas espécies estão sendo afetadas diretamente pelo aumento da temperatura e pelas consequências associadas, como a acidificação do oceano.

A distribuição das temperaturas também revela padrões interessantes. Áreas com correntes marinhas mais intensas estão apresentando variações mais significativas em relação às médias históricas. Isso pode ser atribuído à alteração nos padrões de circulação oceânica, que está afetando a distribuição de nutrientes e oxigênio essenciais para as espécies marinhas.

Aumentos nas temperaturas também estão associados a mudanças nos padrões de reprodução e distribuição de espécies. Peixes e outros organismos estão sendo deslocados ou extintos em áreas onde as condições climáticas não atendem às suas necessidades. Isso tem implicações graves para as cadeias alimentares marinhas e para a saúde dos ecossistemas marinhos.

É importante notar que essas mudanças são consistentes com estudos de caso recentes, como o da costa oeste dos Estados Unidos, onde um aumento na temperatura de 1°C foi associado a uma redução de 30% nas populações de peixes e invertebrados marinhos. Além disso, as regiões mais quentes do Oceano Pacífico estão apresentando mudanças significativas em suas comunidades marinhas, o que pode ter consequências graves para a biodiversidade e a saúde dos ecossistemas.

Em resumo, os dados fornecidos sobre as medidas de temperatura no nível do mar do Oceano Pacífico revelam um quadro sombrio para a vida marinha. As consequências do aquecimento global estão sendo sentidas em todo o ecossistema e é fundamental que sejam tomadas medidas imediatas para proteger esses recursos vitais para a humanidade.
```

## Prompt Engineering

**Prompt Engineering** é o nome dado ao processo de se fazer um prompt eficiente. Para fazer isso bem, é necessário: Análise Crítica, Criatividade e Expertise técnica.

Além disso, é um processo iterativo, ou seja, *pode ser necessário repetir o processo* para se obter o resultado desejado.

## Para que fazer isso?

- Otimizar a eficiência do modelo;
- Melhorar a performance do modelo para tarefas específicas;
- Entender as limitações do modelo;
- Melhorar a segurança ao se utilizar o modelo.

Existe um concenso sobre algumas boas práticas para criação de um bom prompt:

### Clareza

- Usar linguagem clara e concisa;
- Evitar jargões e termos complexos;
- Dar instruções explícitas.

### Contexto: 

- Forneça um contexto;
- Inclua informações relevantes.

### Precisão:

- Seja específico;
- Use exemplos.

### Role-play:

- Forneça um contexto para um role-play, e assuma um papel como Desenvolvedor, Empresário, Estudante de Direito e etc.

## Training/treinamento:

O treinamento é outro modo de se influenciar nas probabilidades do vocabulário de um modelo. Ele costuma ser usado quando: existem dados para treinamento e a adaptação de domínio é necessária (adaptar um modelo, costumeiramente via treinamento, para melhorar a performance dele em uma área na qual ele não foi treinado).

## Groundedness, Attributability e Hallucinations

Hallucination é o nome dado ao texto gerado por LLMs que não são factuais ou não suportados pelos dados usados no treinamento do modelo. **Não existe uma maneira de eliminar definitivamente esse problema, mas apenas reduzir sua ocorrência**.

## Groundedness and Attributability

São formas de evitar as “hallucinations”, fazendo com que o modelo aprenda a citar e se basear nas fontes do texto que ele gerou.