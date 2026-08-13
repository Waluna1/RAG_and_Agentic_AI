Introduction
A leading AI startup building a next-generation Connoisseur Companion. Unlike traditional recommendation systems that rely on coarse 1–5 star ratings, the organization
aims to understand the why behind user preferences, capturing the vibe of a restaurant, dietary considerations, and standout “hero dishes” hidden inside unstructured, 
multimodal data.
The below gives the stages for the creation of a recommendation system described above. The below outlines the construction of the system. The completed jupyter notebook 
files are included in the folder, with their accompanying names. The titles for each stage are the representational names of the note books.
1. Structure Text and Multimodal Data with LLMs
In this phase, you will use LLMs to transform unstructured restaurant descriptions into structured JSON files by designing prompts and extracting predefined 
attributes. You will apply multimodal LLMs to generate captions from review images and integrate those captions into structured user review data. Finally, you will 
build a command-line Python interface to browse, add, edit, and delete restaurant records, integrate LLM-powered structuring functions for new entries, and implement 
file backup mechanisms before saving updates.
2. M1L2_Process_Multimodal_Data_with_LLMs
Building on the structured JSON knowledge base you created in phase 1, this section extends your GenAI data pipeline beyond text by incorporating visual data. You will
work with food recipe images, recipe metadata, and user visit history, and use vision-enabled LLMs to convert visual information into meaningful textual descriptions 
that enrich your existing structured JSON data. This phase focuses on extending GenAI-powered data pipelines beyond text by using image captioning to enrich structured
JSON data, enabling more comprehensive and explainable recommendation systems.
3. M2L1_Lab
Retrieval-Augmented Generation (RAG) systems depend critically on the quality of their retrieval layer to produce grounded and contextually accurate responses. In 
real-world applications, user queries often span heterogeneous data sources, including structured textual information and visual content. As a result, modern RAG 
pipelines increasingly adopt multimodal retrieval architectures capable of indexing and searching across multiple data modalities.
To support these scenarios, multimodal systems encode different data types into dense vector representations that enable efficient similarity-based search. A 
well-designed retrieval layer ensures that high-quality evidence is identified before any downstream reasoning or generation occurs.
In this lab, you will build the retrieval backbone of a multimodal RAG system for restaurant and food discovery. Using structured outputs from Module 1 together with 
raw food images, you will construct vectorized, searchable indexes that support cross-modal evidence retrieval.
The lab emphasizes retrieval pipeline engineering, focusing on how heterogeneous data is transformed, embedded, and organized within scalable vector databases using 
ChromaDB. This modular design mirrors production RAG systems, where the retrieval layer operates as a reusable component independent of the generation model.
Upon completion, you will have a functional multimodal vector index that forms the foundation for similarity search, metadata-constrained retrieval, and multimodal 
fusion.
4. M2L2_Lab
You constructed multimodal vector indexes for restaurant articles and food images using Chroma. With the indexing infrastructure established, the next step is to 
operationalize the retrieval layer, which is responsible for identifying relevant content at query time.
Similarity search forms the backbone of modern Retrieval-Augmented Generation (RAG) systems by enabling semantic matching between user queries and stored vector 
representations. However, in real-world applications, similarity alone is often insufficient. Production systems frequently require structured constraints, such as 
filtering by location, cuisine, or content source, to ensure that retrieved results satisfy business rules or user preferences.
To address this need, modern retrieval pipelines combine vector similarity with metadata-aware filtering. This hybrid strategy allows systems to narrow the candidate 
search space while preserving semantic relevance, improving both controllability and precision. Such designs are widely used in recommendation engines, multimodal 
search platforms, and large-scale RAG deployments.
In this lab, you will implement similarity-based top-k retrieval with optional metadata constraints over the persisted Chroma collections. You will perform semantic 
retrieval over restaurant articles and similarity search over the food image collection, observing how structured filters influence the final ranked results.
By the end of this lab, you will have built a reusable hybrid retrieval workflow that mirrors production systems. This retrieval layer will serve as the foundation 
for multimodal fusion and re-ranking in the next lesson.
5. M2L3_Lab
Earlier, you built the multimodal retrieval backbone by constructing vector indexes for restaurant articles and food images. You then operationalized these indexes by 
performing similarity-based retrieval with optional metadata filtering. At that stage, ranking was performed independently within each modality.
In this phase, you take the next step toward a production-grade multimodal retrieval system. Real-world RAG pipelines rarely rely on a single evidence source. Instead,
they retrieve candidates from multiple modalities and fuse them into a unified ranking that better reflects overall relevance.
To enable this, the lab introduces cross-modal score normalization and fusion. Because similarity scores produced by different embedding models 
(for example, Sentence-Transformers versus CLIP) are not directly comparable, they must first be calibrated onto a common scale. You'll then apply a weighted fusion 
strategy to combine evidence from text and image retrieval into a single ranked list.
You'll design and implement a practical multimodal fusion pipeline that mirrors real production systems. This includes retrieving candidates from both modalities, 
normalizing their scores, applying weighted fusion, and optionally enforcing metadata constraints to support controllable, precision-oriented retrieval.
By the end of the lab, you will have a unified multimodal ranking pipeline capable of intelligently prioritizing heterogeneous evidence sources.
6. M3L1_Design_Specialized_Agents
In this phase of the project, you will design a multi-agent system for restaurant and recipe recommendations. You will define six specialized agents, each with a 
6.1 distinct role in the recommendation pipeline:
6.2 User Profile Generator: Analyzes user data to extract preferences and patterns
6.3 RAG Retriever: Queries vector databases for relevant restaurants and recipes
6.4 Food Trend Analyst: Identifies current food trends and popular ingredients
6.5 Food Style Expert: Analyzes cuisines, cooking methods, and flavor profiles
6.6 Nutrition Expert: Evaluates nutritional content and dietary restrictions
6.7 Recommendation Expert: Synthesizes all insights into final recommendations
By breaking down the recommendation task into specialized roles, you create a modular, maintainable system where each agent focuses on what it does best.
7. M3L2_Implement_Multi_Agent_Systems
Earlier, you designed six specialized agents. In this lab, you will integrate them into a coordinated workflow that generates restaurant and recipe recommendations.
You will implement a hybrid workflow with four phases:
7.1 User Analysis (Sequential): Generate a user profile
7.2 Data Retrieval (Sequential): Query the vector database
7.3 Analysis (Parallel): Analyze trends, food styles, and nutrition simultaneously
7.4 Synthesis (Sequential): Generate final recommendations
7.5 By the end of this lab, you will have a working multi-agent system that you can test with a variety of user inputs.
8. Build a Chatbot Interface for the Recommendation System
In this phase, you will build a chatbot interface for your multi-agent recommendation system using Gradio. The chatbot will:
8.1 Understand user requests in natural language
8.2 Classify whether users want restaurant or recipe recommendations
8.3 Extract preferences like cuisines, dietary restrictions, and price range
8.4 Invoke the multi-agent workflow from Lesson 2
8.5 Present recommendations in a conversational, engaging format
8.6 Allow users to add, update, and delete items in the database
8.7 By the end of this lab, you will have a fully functional chatbot that anyone can use without writing code.
