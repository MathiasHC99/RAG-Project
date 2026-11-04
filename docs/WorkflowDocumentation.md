# n8n workflows

| Workflow export | Purpose | Screenshot |
|---|---|---|
| [Recipes Into Both Databases](../Workflow%20JSON/Recipes%20Into%20Both%20Databases.json) | Generates embeddings and writes vector and graph recipe data to Neo4j. | [Data ingestion](../Screenshots/Recipes%20to%20databases.png) |
| [Vector Recipe Search](../Workflow%20JSON/Vector%20Recipe%20Search.json) | Embeds `query` and searches `recipe_embeddings`. | [Vector retrieval](../Screenshots/Vector%20search.png) |
| [Graph Recipe Search](../Workflow%20JSON/Graph%20Recipe%20Search.json) | Filters candidate recipes by IDs, ingredients, dietary tags, and time. | [Graph retrieval](../Screenshots/Graph%20search.png) |
| [Recipe RAG AI Agent](../Workflow%20JSON/Recipe%20RAG%20AI%20Agent.json) | Connects chat to the model, memory, and both retrieval tools. | [Agent connections](../Screenshots/AI%20agent.png) |

The agent's [execution trace](../Screenshots/Agent%20tool%20connections.png) shows its tools being called.
