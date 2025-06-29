# Shell in C
#programming/project/c

Shell Traits:
* Initialize: reads and executes configuration files. These change aspects of the shell's behavior
* Interpret: shell reads commands from stdin and executes
* Terminate: After it's commands are executed, the shell executes and shutdown commands frees up any memory, and terminates

**Main block:**

```C
int main(int argc, char **argv)
    {
      // Load config files, if any.
         
      // Run command loop. This is the actual program call
      lsh_loop();
    
      // Perform any shutdown/cleanup.
    
      return EXIT_SUCCESS;
    }
```