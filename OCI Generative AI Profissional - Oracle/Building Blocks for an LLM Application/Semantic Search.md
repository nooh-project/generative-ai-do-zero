Tipo de pesquisa feito pelo significado das palavras. O retrieval é feito pelo entendimento da intenção do usuário e do contexto, no lugar de matches de palavras.

Existem duas formas de se fazer isso:

- Dense Retrieval
- Reranking

### Dense Retrieval

Baseada nos embeddings tanto da query quanto dos documentos, para identificar e selecionar os documentos relevantes para uma determinada query. Isso possibilita um sistema de recuperação baseado no entendimento e compatibilidade das similaridades entre queries e documentos.

### Reranking

Determina um valor de relevância para o par query-respostas a partir das buscas iniciais. Define como os resultados corretos, os que tem maiores valores de relevância. Costuma ser implementado via um LLM treinado.

## Hybrid Search = Sparse + Dense

Combina a busca de keywords (sparse) e a busca semântica (dense) visando, respectivamente, conseguir resultados amplos e a partir deles refinar até serem obtidos os mais relevantes.