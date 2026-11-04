# Neo4j data and setup

## Data files

- [`recipes-graph.csv`](./recipes-graph.csv): structured recipe fields.
- [`recipes-vector.csv`](./recipes-vector.csv): text used for semantic search.

## Data model in the ingestion workflow

| Node | Properties |
|---|---|
| `graph` (recipe) | `id`, `title`, `description`, `minutes`, `source`, `instructions`, `cuisine`, `ingredients`, `dietaryTags` |
| `Ingredient` | `name` |
| `Cuisine` | `name` |
| `DietaryTag` | `name` |
| `Recipe` (vector) | `id`, `title`, `text`, `minutes`, `source`, `embedding`, `embeddingModel` |

Relationships: `(:graph)-[:USES]->(:Ingredient)`, `(:graph)-[:IN_CUISINE]->(:Cuisine)`, and `(:graph)-[:HAS_TAG]->(:DietaryTag)`.



## Rebuild notes

1. Start Neo4j, n8n, and Ollama; configure credentials in n8n.
2. Ensure the `graphdb` and `vectordb` databases exist on the same Neo4j server. With admin access, create missing databases from the `system` database:

   ```cypher
   CREATE DATABASE graphdb IF NOT EXISTS;
   CREATE DATABASE vectordb IF NOT EXISTS;
   ```

3. In `vectordb`, create the vector index using the statement below if it does not already exist.
4. Import and run [Recipes Into Both Databases](../Workflow%20JSON/Recipes%20Into%20Both%20Databases.json).
5. Verify graph nodes/relationships in `graphdb`, and vector nodes/embeddings plus an `ONLINE` index in `vectordb`.


## Environment and index

- Neo4j: `2026.10.1`
- n8n: `2.36.7`
- Ollama: `0.40.0`
- Chat model: `qwen3.5:4b`
- Embedding model: `nomic-embed-text:v1.5` (768 dimensions)
- Databases: `vectordb` for vector search; `graphdb` for graph search
- Vector index: `recipe_embeddings` in `vectordb`

The index is `ONLINE`, 100% populated, and indexes `Recipe.embedding` with 768 dimensions. Its configuration uses cosine similarity, search expansion factor `3.0`, HNSW `m: 16`, construction factor `100`, and binary quantization.

Screenshot: [Neo4j vector index](../Workflow%20Screenshots/Neo4j%20vector%20index.png) and [index definition](../Workflow%20Screenshots/Neo4j%20vector%20index%20definition.png).

Neo4j-reported index creation statement (`SHOW INDEXES` → `createStatement`):

```cypher
CREATE VECTOR INDEX `recipe_embeddings` FOR (n:`Recipe`)
ON (n.`embedding`) OPTIONS {indexConfig: {
  `vector.default_search_expansion_factor`: 3.0,
  `vector.dimensions`: 768,
  `vector.hnsw.ef_construction`: 100,
  `vector.hnsw.m`: 16,
  `vector.quantization.type`: 'BINARY',
  `vector.similarity_function`: 'COSINE'
}}
```

