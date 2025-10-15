# Agent Development Kit (ADK)

Agent Development Kit (ADK) is a flexible and modular framework for developing and deploying AI agents. While optimized for Gemini and the Google ecosystem, ADK is model-agnostic, deployment-agnostic, and is built for compatibility with other frameworks. ADK was designed to make agent development feel more like software development, to make it easier for developers to create, deploy, and orchestrate agentic architectures that range from simple tasks to complex workflows.


## 🚀 Installation

You can install the latest stable version of ADK using `pip`:

```bash
pip install google-adk
```

## Create an agent project¶
Run the adk create command to start a new agent project.

```bash
adk create my_agent
```

## Explore the agent project
The created agent project has the following structure, with the agent.py file containing the main control code for the agent.

```bash
my_agent/
    agent.py      # main agent code
    .env          # API keys or project IDs
    __init__.py
```
## Update your agent project¶
The agent.py file contains a root_agent definition which is the only required element of an ADK agent. You can also define tools for the agent to use. Update the generated agent.py code to include a get_current_time tool for use by the agent, as shown in the following code:


```bash
from google.adk.agents.llm_agent import Agent

# Mock tool implementation
def get_current_time(city: str) -> dict:
    """Returns the current time in a specified city."""
    return {"status": "success", "city": city, "time": "10:30 AM"}

root_agent = Agent(
    model='gemini-2.5-flash',
    name='root_agent',
    description="Tells the current time in a specified city.",
    instruction="You are a helpful assistant that tells the current time in cities. Use the 'get_current_time' tool for this purpose.",
    tools=[get_current_time],
)
```


## run in terminal

```bash
run .\my_agent\
```

## run in web

```bash
adk web
```