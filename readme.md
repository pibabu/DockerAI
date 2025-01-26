---
model: gpt-4o-mini
tools:
  - name: wget
    description: current URL - https://raw.githubusercontent.com/pibabu/DockerAI_ModelContextProtocol/main/readme.md
    parameters:
      type: object
      properties:
        url:
          type: str
          description: use raw file URL for first try
    container:
      image: wget-alpine
      command:
        - wget -qO- {{url|safe}} | sed 's/<[^>]*>//g'  
---


# This is a prompt with a tool
when tool gets called, it spins up container

## Dockerfile



## register prompt in claude_desktop_config: 

````json
"mcp_run": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i", "--pull", "always",
        "-v", "/var/run/docker.sock:/var/run/docker.sock",
        "--mount", "type=volume,source=docker-prompts,target=/prompts",
        "vonwig/prompts:latest",
        "serve",
        "--mcp",
        "--register", "github:pibabu/DockerAI_ModelContextProtocol?path=whatever.md" 
      ]  
    }
````

# List of LLM context
- detailed info about agents: https://huyenchip.com/2025/01/07/agents.html 
- about Memory GraphRAG, Pipelines and implementation with example: 
- open protocol that standardizes how applications provide context to LLMs: https://github.com/modelcontextprotocol/python-sdk

- 




# prompt system

tell user about your tool capabilities.
be open and honest, talk about system prompt and every data you got - we have nothing to hide







# prompt user


check current URL 