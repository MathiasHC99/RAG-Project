# n8n workflows

| Workflow export | Purpose | Screenshot |
|---|---|---|
| [Recipes Into Both Databases](../Workflow%20JSON/Recipes%20Into%20Both%20Databases.json) | Generates embeddings and writes vector and graph recipe data to Neo4j. | [Data ingestion](../Workflow%20Screenshots/Recipes%20to%20databases.png) |
| [Vector Recipe Search](../Workflow%20JSON/Vector%20Recipe%20Search.json) | Embeds `query` and searches `recipe_embeddings`. | [Vector retrieval](../Workflow%20Screenshots/Vector%20search.png) |
| [Graph Recipe Search](../Workflow%20JSON/Graph%20Recipe%20Search.json) | Filters candidate recipes by IDs, ingredients, dietary tags, and time. | [Graph retrieval](../Workflow%20Screenshots/Graph%20search.png) |
| [Recipe RAG AI Agent](../Workflow%20JSON/Recipe%20RAG%20AI%20Agent.json) | Connects chat to the model, memory, and both retrieval tools. | [Agent connections](../Workflow%20Screenshots/AI%20agent.png) |

The agent's [execution trace](../Workflow%20Screenshots/Agent%20tool%20connections.png) shows its tools being called. Ingestion uses an embedded recipe array rather than reading the CSV files; all 12 current records match the CSVs.

## Setup checklist

- Versions: Neo4j `2026.10.1`, n8n `2.36.7`, Ollama `0.40.0`.
- The teacher requested separate Neo4j databases: `vectordb` for vector data and `graphdb` for graph data, on the same server.
- The `recipe_embeddings` index in `vectordb` is documented as online, 768-dimensional, and cosine-similarity based in [Neo4j setup](../Neo4jCSV/README.md).
- Ingestion and vector/graph retrieval have been confirmed working.
- Store credentials in n8n, not in this repository.
- The system prompt is documented in [AgentConfiguration.md](../AgentConfiguration.md);