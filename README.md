# PreventiveCareAI  
### AI-Powered Preventive Healthcare Assistant using IBM watsonx.ai  

---

## Overview  
**PreventiveCareAI** is a retrieval-augmented, conversational AI assistant that simplifies access to preventive healthcare information.  
Built on **IBM watsonx.ai**, the project demonstrates how large language models (LLMs) and semantic retrieval can transform trusted health documents into an interactive, multilingual, and evidence-based chatbot.

The system uses two official public-health documents:  
- **CDC Adult Immunization Schedule (2025)**  
- **Physical Activity Guidelines for Americans (2nd Edition)**  

It provides accurate, cited responses to user questions such as:  
> “What vaccines are recommended for adults over 65 years?”  
> “How much physical activity should adults get each week?”  

---

## Notebook Pipelines  

The project is organized into **two Jupyter Notebooks**, each handling a separate retrieval pipeline:

| Notebook | Description |
|-----------|--------------|
| **`immunization-pipeline.ipynb`** | Builds the AI retrieval workflow for the *Adult Immunization Schedule*. It handles document ingestion, vector embedding using `intfloat/multilingual-e5-large`, and retrieval through Chroma. The notebook defines the `get_pdf_context_immunization` tool that powers immunization-related queries. |
| **`physical-health-pipeline.ipynb`** | Implements the retrieval workflow for the *Physical Activity Guidelines*. It creates embeddings, indexes the text, and exposes the `get_pdf_context_physical_activity` tool for exercise- and activity-related questions. |

Each pipeline runs independently but can be combined into a single unified chatbot that intelligently selects the correct retrieval path based on the user’s question.

---

## Technology Stack  

| Component | Description |
|------------|-------------|
| **Platform** | IBM watsonx.ai |
| **LLM** | `ibm/granite-3-2-8b-instruct` |
| **Embedding Model** | `intfloat/multilingual-e5-large` |
| **Vector Database** | Chroma |
| **Framework** | LangChain |
| **Programming Language** | Python |
| **Environment** | IBM watsonx.ai Managed Notebook |
| **Data Source** | Healthcare PDFs stored as watsonx.ai Data Assets |

---

## Solution Design  

1. **Document Preparation**  
   - Healthcare PDFs are uploaded and managed as **Data Assets** in watsonx.ai.  
   - Each notebook preprocesses and embeds text chunks into vectors for semantic retrieval.  

2. **Retrieval & Reasoning**  
   - The system retrieves contextually relevant chunks using the Chroma vector store.  
   - A watsonx.ai LLM (`granite-3-2-8b-instruct`) generates answers **grounded in the retrieved context**.  

3. **AI Agent Architecture**  
   - The LLM functions as an **AI agent**, deciding which retrieval tool to use, invoking it, and synthesizing the final answer.  

4. **Multilingual Support & Memory**  
   - Queries in non-English languages trigger translation to and from the user’s language.  
   - **Conversation memory** maintains context for follow-up questions.  

---

## Target Users  

- **Public health educators** promoting preventive care awareness  
- **Healthcare professionals** providing patient education  
- **General citizens** seeking trusted, easy-to-understand guidance  

While currently demonstrated as a notebook-based prototype, the system can be **scaled into a web or mobile chatbot interface** for wider deployment.

---

## Impact  

PreventiveCareAI bridges the gap between complex healthcare literature and everyday understanding.  
By combining **Watsonx LLM reasoning**, **multilingual embeddings**, and **AI agent orchestration**, it delivers accurate, explainable, and cited preventive-care insights — empowering individuals to make informed health decisions and supporting public health outreach at scale.

---

## License  
This project is developed for educational and demonstration purposes using IBM watsonx.ai.  
© 2024 PreventiveCareAI Team. All rights reserved.
