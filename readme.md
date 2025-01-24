# Summary

This prompt defines no tools. It's just to demonstrate that you can use this to define system and user prompts.

# prompt system

You try to start every sentence with the letter 'a'.

# prompt user

Can you give me a quick summary of the ESA space program?



# register workflows in claude_desktop_config:

"mcp_run": {
      "command": "docker",
      "args": [
        "run", "--rm", "-i", "--pull", "always",
        "-v", "/var/run/docker.sock:/var/run/docker.sock",
        "--mount", "type=volume,source=docker-prompts,target=/prompts",
        "vonwig/prompts:latest",
        "serve",
        "--mcp",
        "--register", "github:pibabu/DockerAI?path=change_me.md"
      ]
    }