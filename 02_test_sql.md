---
tools:
  - name: docker
    description: run any docker command with arguments
    parameters:
      type: object
      properties:
        args:
          type: array
          items:
            type: string
          description: arguments to pass to the docker CLI
    container:
      image: docker:cli
      command:
        - "{{args|into}}"
model: gpt-4o-mini
---

# prompt user

 use the docker command to start up a mysql server running on port 8080...test if it works