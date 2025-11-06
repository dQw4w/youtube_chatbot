# 🎥 YouTube Chatbot

This project builds a **semantic search and Q&A chatbot** for YouTube channels.
It fetches video transcripts, embeds them using OpenAI embeddings, stores them in **Qdrant** (a vector database), and performs **semantic retrieval** to answer user questions about video content.

---

## 🚀 Project Overview

Run the notebooks in the following order:

1. **`fetch_data.ipynb`** → Fetch video metadata and subtitles (you will only need to run it once per youtube channel)
2. **`embed.ipynb`** → Generate embeddings and store them in Qdrant (you will only need to run it once per youtube channel)
3. **`inference.ipynb`** → Query the vector database and get AI-generated answers

> ⚠️ **Note:**
> The “Download subtitles” section in `fetch_data.ipynb` is **not yet complete**, so fetching new subtitles currently **does not work**.
> To test the workflow, you can use the pre-fetched dataset:
>
> ```
> bluepigeon0810.jsonl
> ```
>
> (This file contains data for the YouTube channel *蒼藍鴿的醫學天地*.)

---

## 🧩 Setup Instructions

### 1. Set Up Required API Keys

You’ll need **three keys**:

* `QDRANT_URL`
* `QDRANT_API_KEY`
* `OPENAI_API_KEY`

You’ll fill these in both `embed.ipynb` and `inference.ipynb`.

#### 🧠 OpenAI API Key (for ChatGPT and text embedding)

1. Go to [OpenAI Platform](https://platform.openai.com/).
2. Log in → [API Keys](https://platform.openai.com/settings/organization/api-keys).
3. Click **Create new secret key** and copy it.
4. Use it as:

   ```python
   OPENAI_API_KEY = "your_openai_api_key"
   ```

> ⚠️ **Note:**
> Each account has a limited amount of free quota, so use it carefully. Running embed.ipynb and inference.ipynb both burns your quota. We will switch to free ai models in the future.


#### 🗄️ Qdrant API Key and URL (for vector database)

1. Register for a free Qdrant Cloud account at [qdrant.tech](https://qdrant.tech/).
2. Go to **Dashboard → Clusters**, and **create a new cluster**.
3. Click into your cluster and find:

   * **QDRANT_URL:** In the *Use the API* section, copy the *Endpoint URL*.
   * **QDRANT_API_KEY:** Under *API Keys → Create*, then copy the key.
4. Use them as:

   ```python
   QDRANT_URL = "your_qdrant_url"
   QDRANT_API_KEY = "your_qdrant_api_key"
   ```

---



