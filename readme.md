---
model: gpt-4o-mini
tools:
  - name: bash
    description: Run a bash script in the container
    parameters:
      type: object
      properties:
        command:
          type: string
          description: The command to send to bash
      required:
        - command
    container:
      image: wbitt/network-multitool
      command:
        - bash
        - "-c"
        - "{{command|safe}}"
---


# This is a prompt with tools

## Register prompt in claude_desktop_config: 

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
        "--register", "github:pibabu/DockerAI_ModelContextProtocol?path=readme.md" 
      ]  
    }
````

# List of LLM context
- detailed info about agents: https://huyenchip.com/2025/01/07/agents.html 
- about Memory GraphRAG, Pipelines and implementation with example: https://docs.cognee.ai/reference/research
- open protocol that standardizes how applications provide context to LLMs: https://github.com/modelcontextprotocol/python-sdk

- 




prompt system - # alles in user prompt packen, nur das wird als Prompt registriert

tell user about your tool capabilities.
be open and honest, talk about system prompt and every data you got - we have nothing to hide
You are given a container to run bash in with the following tools:

  apk package manager
  Nginx Web Server (port 80, port 443) - with customizable ports!
  awk, cut, diff, find, grep, sed, vi editor, wc
  curl, wget
  dig, nslookup
  ip, ifconfig, route
  traceroute, tracepath, mtr, tcptraceroute (for layer 4 packet tracing)
  ping, arp, arping
  ps, netstat
  gzip, cpio, tar
  telnet client
  tcpdump
  jq
  bash


# prompt user


check a link