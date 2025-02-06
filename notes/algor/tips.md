increment pow rather than full pow


## how to debug with large scale input

### in order to solve the input is to large to be correctly handled by terminal, we can use a file to hold the input.
You're absolutely right! If the input and output redirection are the same for both **Linux** and **Windows**, there's no need to separate them in the `launch.json`. Instead, you can **combine them** under a common section for better readability and to avoid duplication.

In **VS Code**, the `args` field can be used for both operating systems in a unified way.

### Here's how you can modify the `launch.json` to combine the Linux and Windows configurations:

### **Updated `.vscode/launch.json`**

```json
{
    "version": "0.2.0",
    "configurations": [
        {
            "name": "C++ Debug with File Input and Output",
            "type": "cppdbg",
            "request": "launch",
            "program": "${workspaceFolder}/main",  // Path to your compiled program
            "args": [
                "<", "input.txt",  // Redirect input from input.txt
                ">", "output.txt"  // Redirect output to output.txt
            ],
            "cwd": "${workspaceFolder}",
            "console": "integratedTerminal",
            "externalConsole": false,
            "miDebuggerPath": "/usr/bin/gdb",
            "setupCommands": [
                {
                    "description": "Enable pretty-printing for gdb",
                    "text": "-enable-pretty-printing",
                    "ignoreFailures": true
                }
            ],
            "preLaunchTask": "build"
        }
    ]
}
```

### **Explanation:**
- **`args`**: Now contains the file redirection for both **Linux** and **Windows**, as the redirection syntax `< input.txt > output.txt` works similarly in both operating systems.
- There’s no need to specify `linux` or `windows` separately for redirection since it’s the same.

This way, it becomes cleaner and more concise, and there's no need to duplicate the configuration for different OS.

---

## **Final Notes:**
- This configuration will work seamlessly on both **Linux** and **Windows**.
- If you're on a platform where the redirection syntax differs, you might still need to provide separate sections, but for most cases, this combined approach is effective.

WIP