---
model: gpt-4o-mini
tools:
  - name: file 
    description: |
      read a file from disk
      Read the complete contents of a file from the file system.
      Handles various text encodings and provides detailed error messages
      if the file cannot be read. Use this tool when you need to examine
      the contents of a single file. Only works within allowed directories.
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
      Create a new file or completely overwrite an existing file with new content.
      dont escape newlines! no \n ! just answer with string
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
  - name: list
    
---

# prompt user

write blabla in example.txt...just one tool call! if it fauils, surrender