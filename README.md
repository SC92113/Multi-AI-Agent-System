# Multi-AI-Agent-Systems

### 🛠️ This project is supported by [DeepLearning.AI](https://www.deeplearning.ai/) and [crewAI](https://www.crewai.com/).

## ☰ Table of Contents
- [Goal](https://github.com/SC92113/Multi-AI-Agent-System/tree/main?tab=readme-ov-file#-goal)
- [Key concepts in the projects](https://github.com/SC92113/Multi-AI-Agent-System/tree/main?tab=readme-ov-file#-key-concepts-in-the-projects)
  - [General AI agentic flow](https://github.com/SC92113/Multi-AI-Agent-System/tree/main?tab=readme-ov-file#general-ai-agentic-flow)
  - [Principles for defining a good agent](https://github.com/SC92113/Multi-AI-Agent-System?tab=readme-ov-file#principles-for-defining-a-good-agent)
  - [crewAI agentic process](https://github.com/SC92113/Multi-AI-Agent-System?tab=readme-ov-file#crewai-agentic-process)
  - [crewAI set up](https://github.com/SC92113/Multi-AI-Agent-System?tab=readme-ov-file#crewai-set-up)
  - [crewAI tool packages](https://github.com/SC92113/Multi-AI-Agent-System?tab=readme-ov-file#crewai-tool-packages)
- [References](https://github.com/SC92113/Multi-AI-Agent-System/tree/main?tab=readme-ov-file#-references)
- [Research papers](https://github.com/SC92113/Multi-AI-Agent-System/tree/main?tab=readme-ov-file#-research-papers)

## 🎯 Goal
- ### Build a crew of AI agents to execute their own tasks as a whole
- ### Quick access to projects (jupyter notebook)
  - ### [Customize a research writing](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Research_Writing_Agent.ipynb)
  - ### [Customize resume](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Resume_Customization_Agent.ipynb)
  - ### [Customize an outreach campaign](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Customer_Outreach_System_Agent.ipynb)
  - ### [Automate customer support](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Customer_Support_Automation.ipynb)
  - ### [Automate event planning](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Event_Planning_Automation_Agent.ipynb)
  - ### [Automate financial analysis](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Financial_Analysis_Agent.ipynb)

## 💡 Key concepts in the projects
- ### General AI agentic flow
  - Breakdown a task into smaller ones for multiple agents to execute
  - A crew of agents can optimize existing prompting by one central agent
  - Task from human > Agents with tools and processes > Response by LLMs

- ### Principles for defining a good agent
  - **Role playing**
    - Each agent has a specific title and context that focus on specific task
  - **Focus**
    - Each agent focuses to execute its task only
  - **Tool**
    - Each agent has a set of specific tools
    - Property 1 - Versatile
      - Multi-function, can manage all types of inputs and respond with strong outputs
    - Property 2 - Fault-tolerant
      - Continue to execute and send error messages back to agent for correction
    - Property 3 - Caching
      - Store the same previous task requests, avoid hitting API rate limit, and save time to execute
      - e.g. Cross caching layer
  - **Collaboration**
    - All agents can talk to each other to collaborate, delegate tasks, and execute the main task as a whole
  - **Guardrail**
    - Default in crewAI framework
    - Prevent AI hallucination
    - Ensure agents achieve their tasks
  - **Memory**
    - Type 1 - Short term memory
      - During crew execution
    - Type 2 - Long term memory
      - After crew execution, for self-improvement and reuse 
    - Type 3 - Entity memory
      - During crew execution
      - Divided by categories, e.g. person name, org name, etc

- ### crewAI agentic process
  - **Step 1: Defining tools**
    - Agent level tools
      - Agent-specific and can be used when an agent execute its tasks
    - Task level tools 
      - Task-specific and can only be used when that task is executed
  - **Step 2: Defining agents**
    - Role
      - A role that the agent plays
    - Goal
      - A goal that the agent should achieve
    - Agent level tools (depend on use cases)
      - A set of tools that can help the agent to work
    - Backstory
      - Detailed description of the background of agent and its role playing 
    - Delegation (depend on use cases)
      - Decide if the agent can delegate tasks to other agents or not
  - **Step 3: Defining tasks**
    - Description
      - A description of the task
    - Expected_output
      - Expected output that the agent should achieve in task
    - Task level tools (depend on use cases)
      - A set of tools that can help the task being executed
      - Can be assigned to multiple agents
    - Agent
      - Agent that is assigned with the task
  - **Step 4: Defining crew**
    - Agent list
      - Order agents by list
      - Ordering is not applicable if the process is in hierarchical
    - Task list
      - Order tasks by list
      - Ordering is not applicable if the process is in hierarchical
    - Process type
      - Decide which process to run a crew of agents
      - In parallel
        - All agents execute their own tasks at the same time, tasks are not dependently executed
      - In series/ sequential
        - Each agent execute its own task one by one before passing to next agent
      - In hierarchical
        - Crew manager agent can delegate tasks to different agents to execute
        - Remark: hierarchical + series/ parallel can happen at the same time
    - Memory (depend on use cases)
      - Decide if storing the memory of the agentic process in terms of short term, long term, entity memory
  - **Step 5: Run crew**
    - Define input
      - Provide an input that meets the variables defined in the Agent and Task 
    - Kickoff crew
      - Run the crew with input
      - Output can be different even the agentic process is run each time with the same input

- ### crewAI set up
  - crewAI installation: [Installing crewAI](https://docs.crewai.com/getting-started/Installing-CrewAI/)
  - Install crewAI
    - `!pip install crewai==0.28.8 crewai_tools==0.1.6 langchain_community==0.0.29`
  - Control warning
    - `import warnings
      warnings.filterwarnings('ignore')`
  - Import crewAI libraries
    - `from crewai import Agent, Task, Crew, Process`
  - Import LLM for building agents, e.g. Openai, Llama
    - `import os
      from utils import get_openai_api_key
      openai_api_key = get_openai_api_key()
      os.environ["OPENAI_MODEL_NAME"] = 'gpt-3.5-turbo'`

- ### crewAI tool packages
  - crewAI tool package: [crewAI tool](https://docs.crewai.com/core-concepts/Tools/)
  - Defined tools
    - Tools provided by crewAI
  - Custom tool
    - A tool that is defined with name and description by user

## 📚 References 
- ### Key LLMs and APIs for running agentic process
  
  - OpenAI: [OpenAI API](https://platform.openai.com/login?launch)
  - Llama: [Llama API](https://www.llama-api.com/)
  - Ollama: [Ollama framework](https://ollama.com/)
  - Mistral AI: [Mistral AI API](https://docs.mistral.ai/api/)
  - Hugging Face: [Hugging Face models](https://huggingface.co/models)
  - Serper: [Google Search API](https://serper.dev/?gad_source=1&gclid=Cj0KCQjw8MG1BhCoARIsAHxSiQnrNkCFKl50asaTMGGs7v7_CqZO11xifflridfnUkHYfErJ2nBh7DIaAnDJEALw_wcB)
    
## 🔎 Research papers
- [Communicative_Agents_for_Software_Development.pdf](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Communicative_Agents_for_Software_Development.pdf)
