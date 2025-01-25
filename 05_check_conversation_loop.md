---
model: gpt-4o-mini
tools:
  - name: read_file
    description: |
      read a file from disk
    parameters:
      type: object
      properties:
        path:
          type: string
    container:
      image: vonwig/bash_alpine
      entrypoint: cat
      command:
        - "{{path|safe}}"
  - name: write_file
    description: |
      Create a new file or append an existing file with new content.
      only output string, no character escaping!
    parameters:
      type: object
      properties:
        path:
          type: string
        content:
          type: string
    container:
      image: vonwig/bash_alpine
      command:
        - "-c"
        - "echo {{content|safe}} >> {{path|safe}}"
---
# only send user message to claude app
# prompt user
use mails.txt



rules:
ask user for feedback. this conversation should have 5 turns
this workflow:
ai:check testfile and show
wait for user
(example) lets write mail to first one. ask whatup?






