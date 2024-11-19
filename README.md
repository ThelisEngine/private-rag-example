# Local RAG Example

[Watch the video tutorial here](https://youtu.be/-ikCYKcPoqU)
[Read the blog post using Mistral here](https://www.timescale.com/blog/build-a-fully-local-rag-app-with-postgresql-mistral-and-ollama/)

This repository contains an example project for building a private Retrieval-Augmented Generation (RAG) application using Llama3.2, Ollama, and PostgreSQL. It demonstrates how to set up a RAG pipeline that does not rely on external API calls, ensuring that sensitive data remains within your infrastructure.

## Fork - Changes

- Upgraded from *psycopg 2* to *psycopg 3*
- Use new ollama structure : *ollama_generate* become *ai.ollama_generate*
- Small refactor to use global variables *DATABASE_HOST* and *OLLAMA_HOST*

## Prerequisites

- Docker
- Python, [psycopg](https://www.psycopg.org/)
- [Ollama](https://github.com/ollama/ollama) (see dedicated installation guide if needed)
- [PostgreSQL](https://docs.timescale.com/self-hosted/latest/install/installation-docker/), [pgai](https://github.com/timescale/pgai)

## PostgreSQL Docker Setup

Use the associated *docker-compose.yml* and start it with:

```bash
docker-compose up
```

Then, connect to your database instance (adapt your credentials if needed):

```bash
apt install postgresql-client
psql -d "postgres://postgres:password@localhost:5432/postgres"
```

To install *ai extension*:
```bash
CREATE EXTENSION IF NOT EXISTS "ai" VERSION '0.4.0' CASCADE;
```

The CASCADE option automatically installs the pgvector and plpython3u extensions. After installation, you can ensure that the correct versions were installed successfully by listing all extensions using this command in psql:

```bash
\dx
```

Then exit the connection using the following command:

```bash
\q
```
