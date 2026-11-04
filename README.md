# Recipe RAG

A recipe assistant that combines semantic vector search with structured graph filters.

## How it works

1. The n8n ingestion workflow embeds recipes and writes vector and graph data to Neo4j.
2. The agent searches vectors first, then checks candidates against recipe facts in the graph.
3. Ollama provides the chat and embedding models.

## Project files

- [Agent prompt, tools, and connections](./AgentConfiguration.md)
- [Neo4j data model and setup](./Neo4jCSV/README.md)
- [Example questions and results](./examples/ExampleResults.md)
- [Workflow descriptions](./docs/WorkflowDocumentation.md)
- [n8n workflow exports](./Workflow%20JSON/)
- [Workflow screenshots](./Workflow%20Screenshots/)
- [Recipe CSV files](./Neo4jCSV/)

## Known setup notes

- The ingestion workflow uses an embedded recipe array rather than reading the CSV files. The 12 embedded records currently match both CSVs; keep them synchronized if either changes.
- Vector and graph data use separate Neo4j databases, `vectordb` and `graphdb`, on the same server as instructed by the teacher.
- Versions, data model, and vector-index configuration are in [Neo4j data and setup](./Neo4jCSV/README.md). Ingestion and both retrieval workflows have been confirmed working.
