# MCP_with_ollama
I building an recent trending topic Model content protocol by anthropic with local large language model
# Airbnb Search Bot

A simple AI agent that helps search for accommodations on Airbnb using the praisonaiagents library with Ollama's LLM models.

## Overview

This project demonstrates how to create an AI agent that can search for Airbnb listings using natural language instructions. The agent uses:

- `praisonaiagents` library to create and manage the agent
- Ollama's `llama3.2` model for processing natural language
- MCP (Model Control Protocol) with the Airbnb module to interact with Airbnb's services

## Installation

1. Install the required packages:

```bash
pip install "praisonaiagents[llm]"
```

2. Make sure you have [Ollama](https://ollama.ai/) installed and running on your system.

3. Pull the required model:

```bash
ollama pull llama3.2
```

## Usage

Create a Python script (e.g., `airbnb_search.py`) with the following code:

```python
from praisonaiagents import Agent, MCP

search_agent = Agent(
    instructions="""You help book apartments on Airbnb.""",
    llm="ollama/llama3.2",
    tools=MCP("npx -y @openbnb/mcp-server-airbnb --ignore-robots-txt")
)

search_agent.start("MUST USE airbnb_search Tool to Search. Search for Apartments in Paris for 2 nights. 04/28 - 04/30 for 2 adults. All Your Preference")
```

Run the script:

```bash
python airbnb_search.py
```

The agent will:
1. Use the Ollama LLM model to understand the search request
2. Interact with Airbnb's search API through the MCP tool
3. Return relevant search results for apartments in Paris

## Customization

You can customize the search query by modifying the parameters in the `search_agent.start()` method:

- Change the location
- Adjust dates and duration
- Modify the number of guests
- Add specific preferences or filters

## Requirements

- Python 3.7+
- Node.js (for running the MCP server)
- Internet connection
- Ollama installed and running

## Troubleshooting

- Ensure Ollama is running and the llama3.2 model is properly installed
- Check that you have necessary permissions to execute npx commands
- Verify your internet connection allows access to Airbnb's services

## License

[Your license information here]

## Acknowledgments

This project uses:
- [praisonaiagents](https://github.com/praison-ai/agents) - Agent framework
- [Ollama](https://ollama.ai/) - Local LLM hosting
- [@openbnb/mcp-server-airbnb](https://www.npmjs.com/package/@openbnb/mcp-server-airbnb) - MCP server for Airbnb interaction
