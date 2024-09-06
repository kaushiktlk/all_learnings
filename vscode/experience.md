# Problems experienced and their solutions

### Import could not be resolved on source
 - this error is shown when VScode cannot find the python module that you're trying to import. The common cause is that a different python interpreter is configured in vscode and you need to update that to the python version you're using.
 - Open command palette (ctrl + shift + P ) and type "Python: Select Interpreter" and select the correct python interpreter.
 - Example: if you created a virtual environment then the correct interpreter will be something like this: /home/kaushik/fullstack/djangoapp/libraryappenv/bin/python
