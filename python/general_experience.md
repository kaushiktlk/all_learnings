# Python General Experience

 1. **Question:** While creating a docker image for any python application, how are the dependencies mentioned? How do people make sure that nothing is left out? Do they keep track of it manually?

    **Answer:** Yes and No.

    using requirements.txt: In development environments, the packages are normally installed using ```pip install``` commands. When the time comes for packaging the application, the ```pip freeze > requirements.txt``` command is used to automatically generate the requirements.txt file needed to create the docker image. This gives a snapshot of all the modules and their version. It has all the top level dependencies and also their sub-dependencies. But using this method might be difficult to maintain because it contains even some transitive dependencies and dependencies used in development which are not needed in production. But there is no way to identify which is which. In this approach, the dependencies are not tracked manually but automatically generated using pip freeze command.

    using requirements.in: In this approach, a requirements.in file is used where the developers list out the top level dependencies. Then a ```pip-compile requirements.in``` command is used to generate a requirements.txt file. Both of these are checked into version control. Using this method if any top level modules need to be added or removed, that can be done in requirements.in (the .in extension denotes input) file and the sub-dependencies are automatically resolved by pip-compile command. This method ensures that at any time, the requirements.txt file contains all the dependencies and only the necessary dependencies. Nothing more and nothing less. This also helps to identify and remove any top level modules used in development if they are not needed for production. So, in this method, the top level dependencies need to be manually tracked by the developer.

 1. **Note:** If the module is not in the virtual environment, Python does not fallback to searching the global installation by default.

 1. **Question:** What is the difference between a shallow copy and a deep copy?

    **Answer:**
      - ```l2 = l1[:]``` creates a **shallow copy** of the list. Copies the outer list structure but not nested objects (references are copied).
      - ```import copy; new_object = copy.deepcopy(original_object)``` creates a **deep copy**. It creates a new object and recursively copies all nested objects. So, any changes to the copy don't affect the original.
      - BONUS: ```l1 = l2``` creates a **reference copy or assignment copy**, not a new list. Both variables point to the same list object in memory. Any changes to the list via one variable affect the other.
   
 1. **Question:** Explain how global keyword is used in python.

    **Answer:** Global Variables can directly be accessed(read) inside a function
    ```
    x = 'Global'
    def read_global():
      print(x)            #This prints 'Global'
    ```

    But global keyword should be used if the global variable should be **modified** inside the function.
    ```
    x = 'Global'
    def modify_global(): x='Tried'; print(x)
    def actually_modify_global(): global x; x='Done'; print(x)
    print(x)                    # prints Global
    modify_global()             # prints Tried inside the function
    print(x)                    # prints Global because global variable is not modified
    actually_modify_global()    # prints Done inside the function
    print(x)                    # prints Done outside the function as well because
                                # the global variable was modified inside the function
    ```
