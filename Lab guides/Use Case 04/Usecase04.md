# Use Case 04- Chatting with your data using AI Skills in Microsoft Fabric

With the Microsoft Fabric AI skill, you can make data more accessible to
your colleagues. You can configure a generative AI system to generate
queries that answer questions about your data. After you configure the
AI skill, you can share it with your colleagues, who can then ask their
questions in plain English. Based on their questions, the AI generates
queries over your data that answer those questions.

The AI skill relies on generative AI, specifically, large language
models (LLMs). These LLMs can generate queries, for example, T-SQL
queries, based on a specific schema and a question. The system sends a
question in the AI skill, information about the selected data (including
the table and column names, and the data types found in the tables) to
the LLM. Next, it requests generation of a T-SQL query that answers the
question. Parse the generated query to first ensure that it doesn't
change the data in any way. Then execute that query. Finally, show the
query execution results. An AI skill is intended to access specific
database resources, and then generate and execute relevant T-SQL
queries.

**Important Note**: This lab will be executed in a simulated environment. Please follow the instructions in your browser after starting the lab from the link below. 

 ###[Click here to launch the lab](https://labs.technofocus.ai/psl/we60kaq)

Passcode- **volts-018**


