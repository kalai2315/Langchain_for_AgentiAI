
**Conversational AI with Memory using LangChain and Gemini**

**##Chat Memory In Langchain**

https://python.langchain.com/v0.2/docs/how_to/chatbots_memory/


**Conversation Chains and Memory with LCEL**

This notebook demonstrates how to build conversational applications using LangChain Expression Language (LCEL) with support for multi-user memory and session management. It includes examples of building LLM chains, integrating memory components, and setting up persistent SQL-based chat message histories. Google Gemini is used as the language model.

**Overview**

LangChain's modular architecture allows for the composition of conversational AI systems using reusable components. This notebook explores the use of LCEL constructs such as RunnableWithMessageHistory, ChatPromptTemplate, and memory systems like ConversationBufferMemory and SQLChatMessageHistory to create dynamic and stateful chatbot interactions.

**Types of Conversation Memory Demonstrated**

This notebook explores several types of conversation memory supported by LangChain, with a focus on practical implementation using LangChain Expression Language (LCEL). The following memory strategies are demonstrated:

**1. ConversationBufferMemory**

What it does: Stores the full message history in memory (RAM) during runtime.

Usage: Used for session-based memory without persistence.

Key Use Case in Notebook: Applied with RunnableWithMessageHistory to simulate multi-user chat with session IDs.

**2. Memory Windowing via Lambda**

What it does: Selectively retains the last k message pairs from the chat history using a custom function.

Usage: Integrated using RunnablePassthrough.assign() and RunnableLambda to trim history dynamically.

Key Use Case in Notebook: Builds a lightweight memory-efficient context before sending to the prompt and model.

**3. SQLChatMessageHistory**

What it does: Stores user-specific chat history persistently in a SQL database (e.g., SQLite).

Usage: Allows conversations to persist across sessions, supporting multi-user chat memory.

Key Use Case in Notebook: Integrated with a session management function get_session_history_db() using SQLite backend.

**4. Multi-User Memory Management**

What it does: Separates conversation history based on session_id, allowing each user to have an isolated memory.

Usage: Implemented with RunnableWithMessageHistory using Gemini as the LLM and SQL-backed memory for each session.

Key Use Case in Notebook: Simulates independent conversations for users like ali123, boby123, etc.

**Additional Notes**

The notebook focuses on stateless chaining using LCEL, where memory is explicitly passed and transformed using functional components.

Memory is not implicitly embedded in the chain but is layered through configurable variables and message injection.

Windowing is implemented using standard Python slicing (messages[-(k+1):]) to simulate memory trimming without needing ConversationBufferWindowMemory.

















