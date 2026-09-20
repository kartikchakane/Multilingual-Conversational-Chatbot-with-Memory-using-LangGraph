# Multilingual-Conversational-Chatbot-with-Memory-using-LangGraph
This project is a conversational AI chatbot built with LangGraph that remembers earlier messages in a conversation. It uses a large language model (Claude or Gemini through their APIs) to generate replies, and it runs entirely in Google Colab.
This project builds a multi-turn chatbot using LangGraph, a framework for creating stateful LLM applications as graphs. The chatbot is a simple graph with a single chatbot node: the user's message enters the graph, the node sends the whole conversation to the language model, and the reply is added back to the conversation state. A message reducer (add_messages) appends each new message to the history instead of overwriting it.

To give the bot memory, the graph is compiled with a SQLite checkpointer. Each conversation is stored under a unique thread_id, so the bot can answer follow-up questions like "What's my name?" using earlier messages, and separate threads keep separate conversations. API keys are loaded securely from Google Colab Secrets instead of being hard-coded in the notebook. Users chat with the bot through an interactive input loop, and replies are streamed back node by node.

Key features

Multi-turn conversations with context retention
Separate conversation threads using thread_id
Graph-based design that is easy to extend with tools, routing or extra nodes
Secure API key handling with Colab Secrets
Runs in Google Colab with no local setup

Technologies used

Python and Google Colab
LangGraph (StateGraph, SqliteSaver checkpointer)
LangChain integrations (langchain-anthropic or langchain-google-genai)
SQLite for conversation storage
Claude or Gemini as the language model

Limitations and future scope

Memory is stored in an in-memory SQLite database, so it resets when the Colab runtime restarts. Using a file-based database would make it persistent.
The bot has no tools yet. Future versions could add web search, document question answering (RAG), or a web interface.
