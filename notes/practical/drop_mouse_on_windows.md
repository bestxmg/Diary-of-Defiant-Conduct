### frequently-used hot key
- **Ctrl + Tab**: Cycle through open tabs in browsers or apps with multiple tabs (e.g., Microsoft Edge, Chrome).

Shift + Arrow keys:
Shift + Right Arrow: Select text one character to the right.

Win + T: This will focus the taskbar, highlighting the first pinned application. You can then use the Arrow keys to move between the pinned icons on the taskbar.

close current tab: Press Ctrl + W or Ctrl + F4.



That's great! Using Windows without a mouse can significantly speed up your workflow once you get used to keyboard shortcuts. Here are some basic tips to help you navigate and control Windows without the mouse:

### 1. **Navigating Windows with the Keyboard**:

- **Alt + Tab**: Switch between open applications. Hold `Alt` and tap `Tab` to cycle through the apps.
- **Win + D**: Minimize or restore all windows to show the desktop.
- **Win + E**: Open File Explorer.
- **Alt + F4**: Close the active window or program.
- **Win + L**: Lock your computer.
- **Win + R**: Open the "Run" dialog to quickly run commands or programs.

### 2. **Using the Start Menu**:
   
- **Win key**: Open the Start Menu.
- **Arrow keys**: Use the arrow keys to navigate through the Start Menu options.
- **Enter**: Open the selected application or folder.
- **Win + X**: Open the "Power User" menu (includes options like Device Manager, Control Panel, and more).
  
### 3. **File Management**:
   
- **Tab**: Switch between different areas or sections (e.g., address bar, files list, etc.) in File Explorer.
- **Arrow keys**: Navigate through files and folders.
- **Enter**: Open a selected file or folder.
- **Ctrl + C**: Copy the selected item.
- **Ctrl + X**: Cut the selected item.
- **Ctrl + V**: Paste the copied or cut item.
- **Delete**: Delete the selected item.

### 4. **Navigating Between Programs and Windows**:
   
- **Alt + Space**: Open the window menu (close, minimize, restore, etc.) for the active window.
- **Ctrl + Tab**: Cycle through open tabs in browsers or apps with multiple tabs (e.g., Microsoft Edge, Chrome).
- **Ctrl + Shift + Esc**: Open the Task Manager.

### 5. **Accessing Context Menus**:
   
- **Shift + F10**: Open the context menu (right-click menu) for the selected item.

### 6. **Accessibility Features**:
   
- **Narrator (Win + Ctrl + Enter)**: Turns on the screen reader to help you navigate by reading out text and other elements.
- **Magnifier (Win + Plus)**: Zoom in on parts of the screen to make text or objects larger.
- **On-Screen Keyboard (Win + Ctrl + O)**: Allows you to use an on-screen keyboard if needed.

### 7. **Windows Shortcut Keys**:
   
- **Win + I**: Open Settings.
- **Win + S**: Open search bar.
- **Ctrl + A**: Select all items in the current window or text field.
- **Ctrl + Z**: Undo an action.
- **Ctrl + Y**: Redo an action.

By learning these keyboard shortcuts and practicing them, you'll become more efficient at using Windows without needing a mouse. Let me know if you need help with specific tasks!

WIP
I see! It sounds like the **AutoHotkey** script is overriding your **Up** arrow key, which is not what you intended. You can avoid that by either modifying the script or using different keys for scrolling.

### 1. **Fixing the Overriding Issue**:
If you still want to use the **Up Arrow** for normal navigation and also want to use it for scrolling, you can **remap the scrolling to other keys**. For example, you could use the **`Ctrl` + `Up Arrow`** combination to scroll up, and **`Ctrl` + `Down Arrow`** for scrolling down.

Here’s how to adjust the **AutoHotkey** script to prevent overriding the **Up Arrow**:

### 2. **Modified AutoHotkey Script** (using different keys):
```ahk
; Use Ctrl + Up Arrow to scroll up
^Up::Send {WheelUp}

; Use Ctrl + Down Arrow to scroll down
^Down::Send {WheelDown}
```

In this version, the **Ctrl + Up Arrow** will simulate scrolling up, and **Ctrl + Down Arrow** will simulate scrolling down, leaving the **Up Arrow** key free for other uses (like navigating through text or pages).

### 3. **Other Key Combinations**:
You can also use other combinations like **Alt + Up Arrow** or **Alt + Down Arrow** for scrolling:

```ahk
; Use Alt + Up Arrow to scroll up
!Up::Send {WheelUp}

; Use Alt + Down Arrow to scroll down
!Down::Send {WheelDown}
```

Here, the **`Alt`** key is used in combination with the arrow keys to simulate scrolling, leaving your regular arrow keys intact.

### 4. **Test the Script**:
Once you’ve updated the script, save it and run it again by double-clicking the `.ahk` file. The keys you choose for scrolling should now work without interfering with your regular keyboard functions.

Let me know if this solution works or if you'd like more adjustments!