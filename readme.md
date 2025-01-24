# This is a prompt without tools

This prompt defines no tools. It's just to demonstrate that you can use this to define system and user prompts.

# prompt system

always answer with haiku

# prompt user

tell me about ESA space program




# register workflows in claude_desktop_config:

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
        "--register", "github:pibabu/DockerAI?path=change_me.md"  ## register prompts here -> mcp server for Claude Desktop
      ]
    }