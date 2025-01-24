---
tools:
  - name: handle_files
    description: |
      Perform file operations such as reading, writing, or listing files and directories.
      Use the 'action' parameter to specify the operation:
      - 'read': Reads the contents of a file.
      - 'write': Overwrites or creates a new file with the specified content.
      - 'list': Lists the contents of a directory.
    parameters:
      type: object
      properties:
        action:
          type: string
          enum: [read, write, list]
          description: The action to perform (read, write, or list).
        path:
          type: string
          description: The path to the file or directory.
        content:
          type: string
          description: The content to write to the file (required for 'write' action).
    required:
      - action
      - path
    container:
      image: vonwig/bash_alpine
      command:
        - "-c"
        - |
          case {{action}} in
          read) cat {{path|safe}} ;;
          write) echo "{{content|safe}}" > {{path|safe}} ;;
          list) ls -l {{path|safe}} ;;
          esac
---

# prompt user

list files in current dir..max 3 tool calls! if it fauils, surrender