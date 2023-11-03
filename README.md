# RAG LangChain template with Astra DB

A basic chain template showing the RAG pattern using
a vector store on Astra DB.

## Setup:

An [Astra DB](https://astra.datastax.com) database is required; free tier is fine.

- You need the database **API endpoint** (such as `https://0123...-us-east1.apps.astra.datastax.com`) ...
- ... and a **token** (`AstraCS:...`).

Also, an **OpenAI API Key** is required. _Note that out-of-the-box this demo supports OpenAI only, unless you tinker with the code._

Provide the connection parameters and secrets through environment variables. Please refer to `.env.template` for the variable names.

## Running the chain

### Within a LangChain app

Assuming you have already created the app (i.e. `langchain app new MyApp; cd MyApp`), this is what you'll need:

```
langchain app add --repo "hemidactylus/langserve_astradb_entomology_rag" --branch main
```

*Important*: adjust the project's `server.py` as instructed in the output of the above.

Now, make sure all required environment variables are set, and run

```
langchain serve
```

that's it. You can now test the new endpoints by opening `http://127.0.0.1:8000/docs`, or visiting directly `http://127.0.0.1:8000/astradb_entomology_rag/playground/`.

Suggestions:

- for a negative test, try `Do birds have wings?`
- for a positive test, try `Do Odonata have wings?`


### Stand-alone

For a standalone usage (outside of `langchain serve`), clone this repo,
`cd` to its root directory, ensure you set all environment variables,
then launch:

```
poetry install
poetry run python main.py
```

> **Note**: In a full application, the vector store might be populated in other ways than what done here.
> The populate step here is done for the demo RAG chains to sensibly work.
