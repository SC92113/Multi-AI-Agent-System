# Multi-AI-Agent-Systems

### 🛠️ This project is supported by [DeepLearning.AI](https://www.deeplearning.ai/) and [crewAI](https://www.crewai.com/).

### 🎯 Goal
- **Build a crew of AI agents to execute their own tasks as a whole**
- **Projects**
  - [Customize a research writing](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Research_Writing_Agent.ipynb)
  - [Customize resume](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Resume_Customization_Agent.ipynb)
  - [Customize an outreach campaign](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Customer_Outreach_System_Agent.ipynb)
  - [Automate customer support](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Customer_Support_Automation.ipynb)
  - [Automate event planning](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Event_Planning_Automation_Agent.ipynb)
  - [Automate financial analysis](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Financial_Analysis_Agent.ipynb)

### 💡 Key concepts in the projects
- **General AI agentic flow**
  - Breakdown a task into smaller ones for multiple agents to execute
  - A crew of agents can optimize existing prompting by one central agent
  - `Task` from human > `Agent` with tools and processes > `Response` by LLMs
  - Process 1 - In parallel
    - All agents execute their own tasks at the same time, tasks are not dependently executed
  - Process 2 - In series/ sequential
    - Each agent execute its own task one by one before passing to next agent
  - Process 3 - In hierarchical
    - Crew manager agent can delegate tasks to different agents to execute
    - Remark: hierarchical + series/ parallel can happen at the same time

- **Principles for defining a good agent**
  - Role playing
    - Each agent has a specific title and context that focus on specific task
  - Focus
    - Each agent focuses to execute its task only
  - Tool
    - Each agent has a set of specific tools
    - Property 1 - Versatile
      - Multi-function, can manage all types of inputs and respond with strong outputs
    - Property 2 - Fault-tolerant
      - Continue to execute and send error messages back to agent for correction
    - Property 3 - Caching
      - Store the same previous task requests, avoid hitting API rate limit, and save time to execute
      - e.g. Cross caching layer
  - Collaboration
    - All agents can talk to each other to collaborate, delegate tasks, and execute the main task as a whole
  - Guardrail
    - Default in crewAI framework
    - Prevent AI hallucination
    - Ensure agents achieve their tasks
  - Memory
    - Short term memory
      - Within crew execution
    - Long term memory
      - After crew execution, for self-improvement and reuse 
    - Entity memory
      - Within crew execution
      - Divided by categories, e.g. person name, org name, etc

- **crewAI agentic process**
  - Step 1: Defining tools 
    - Agent level tools
    - Task level tools
  - Step 2: Defining agents
    - Role
    - Goal
    - Agent level tools (if necessary)
    - Backstory
    - Delegation (if necessary)
  - Step 3: Defining tasks
    - Description
    - Expected_output
    - Task level tools (if necessary)
    - Agent
  - Step 4: Defining crew
    - Agent list
    - Task list
    - Process type
    - Memory (if necessary)
  - Step 5: Run crew
    - Define input
    - Kickoff input
  
- **crewAI set up**
- **Required APIs and LLMs**
- **crewAI key libraries**
- **crewAI tool packages**
  - Defined tools
  - Custom tools

### 📚 References 

### 🔎 Research papers
- [Communicative_Agents_for_Software_Development.pdf](https://github.com/SC92113/Multi-AI-Agent-Systems/blob/93bfe0a33996f1716fea4d6f8eed97e56885b572/Communicative_Agents_for_Software_Development.pdf)
