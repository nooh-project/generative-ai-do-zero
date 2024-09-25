RAG é um framework para geração de texto usando informação adicional de uma fonte externa. No RAG os modelos buscam documentos e passam para um modelo seq2seq (como o encoder-decoder).

Ele é composto dos seguintes componentes:

- Retriever
- Ranker
- Generator

### Retriever

Tem como função buscar fontes de informação de um grande conjunto de textos ou de um banco de dados, para que o modelo tenha informações relevantes, atualizada e precisas que podem não estar presentes no conjunto de dados de treinamento do modelo. Faz uso de várias técnicas de retrieval.

### Ranker

Tem como função avaliar e priorizar as informações pesquisadas pelo retriever, para que o modelo receba as informações de maior qualidade e pertinência. Faz uso de vários algoritmos que avaliam a qualidade do conhecimento buscado.

### Generator

Tem como função gerar textos parecidos com os criados por humanos, com as informações fornecidas pelos outros componentes e com o texto de input fornecido pelo usuário. Visa gerar uma resposta baseada em fatos, precisa, relevante e coerente. Faz uso de LLMs para fabricar o output que será fornecido ao usuário.

## RAG Techniques

### RAG Sequence

- Para cada input, o modelo busca um conjunto de informações relevantes. Desse conjunto, gera uma única respostas que será resulta da combinação de todas as fontes.

### RAG Token

- Para cada parte da respostas, como uma sentença ou palavra, o modelo adquire documentos relevantes. A partir disso, a resposta é gerada incrementalmente de cada documento adquirido a partir de cada parte da resposta.

## RAG Pipeline

- Ingestion

Os documento são divididos em trechos de informação, incorporados e por fim indexados ao banco de dados.

- Retrieval

As informações são buscadas no database, em seguida são selecionados os melhores resultados.

- Generation

A partir dos melhores resultados, o modelo gera a resposta para o usuário.

### RAG Triad

Método para avaliar a eficiência do RAG, ver mais em [https://truera.com/ai-quality-education/generative-ai-rags/what-is-the-rag-triad/](https://truera.com/ai-quality-education/generative-ai-rags/what-is-the-rag-triad/)