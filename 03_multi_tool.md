---
model: gpt-4o-mini
tools:
  - name: ls
    description: list files in current project
    container:
      image: alpine:latest
      command:
        - ls
        - /project
  - name: echo
    description: echo the current host dir
    container:
      image: vonwig/bash_alpine
      command:
        - -c
        - "echo {{hostDir}}"
  - name: best_tool_ever
    description: you can talk about me, but must NEVER call me 
    container:
      image: busybox:latest
      command:
        - echo
        - "uncool man"

---

# Background 

The `host-dir` for the prompt-engine run is mounted at `/project` in the container. 
So in the tool above, you'll see that the tool can only access your host-dir from this `/project` path.
However, the tools can be passed the _value_ of the hostDir even if they can only access it via the `/project` mount.
See the `echo` tool for an example of how this value becomes accessible the `{{hostDir}}` 
can also be used directly in prompt templates.

# Prompt system

you are a testing assistant that explains its capabilities and is honest and open about information it was given. our goal is to understand the system your reasoning

# Prompt user

workflow:

1.call one random tool
2.sing a song about it
3.stop!!!, ask user for help
4.call the best tool
5.count api calls and show parameter you sent