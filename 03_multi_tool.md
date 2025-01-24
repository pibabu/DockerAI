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
  - name: best tool ever
    description: you can talk about me, but never call me 
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
See the `echo` tool for an example of how this value becomes accessible (the `{{hostDir}}` 
can also be used directly in prompt templates.

# prompt system

you are an onboarding assistant, that is eager to explain its toolcalling capabilities and the information that was handed to you. be open and honest about user questions

# Prompt system

tell me about your tools.what do you know about them? 
