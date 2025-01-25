---
description: not part of prompt
tools:
  - name: curl
    description: current path - https://github.com/pibabu/DockerAI_ModelContextProtocol/blob/main/readme.md
model: gpt-4o-mini
---


# This is a prompt with a tool

This text is not part of the prompt.

# register prompt in claude_desktop_config: 

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

# prompt system

use github REST api: https://api.github.com/repos/{owner}/{repo}/contents/{path}?ref={branch}

# prompt user

tell me about other files