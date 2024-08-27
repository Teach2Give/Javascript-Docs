
# Running JavaScript in Visual Studio Code

To start coding in JavaScript using Visual Studio Code (VS Code), you'll need to set up both the IDE and Node.js. This guide will walk you through the process of installing the necessary tools and getting your JavaScript code up and running.

## 1. Installing Visual Studio Code

1. **Download Visual Studio Code**:
    - Navigate to [Visual Studio Code's website](https://code.visualstudio.com/).

2. **Run the Installer**:
    - Download the appropriate installer for your operating system.
    - Launch the installer and follow the setup instructions.
    - Agree to the terms and continue with the default installation options.

3. **Launch Visual Studio Code**:
    - Open the application from your system’s application menu once installation is complete.

## 2. Installing Node.js

Node.js is crucial for executing JavaScript code outside of a web browser. Here’s how to install it:

1. **Check Existing Node.js Installation**:
    - Open a command prompt or terminal:
        - **Windows**: Search for `cmd` in the Start Menu and open it.
        - **macOS**: Open Finder, search for `Terminal`, and launch it.
    - Type the following command:
      ```
      node -v
      ```
    - If Node.js is installed, you’ll see a version number like `v16.51.1`.

2. **Install Node.js** (if necessary):
    - Visit [Node.js official site](https://nodejs.org).
    - Download the recommended version for your OS.
    - Run the installer and follow the instructions.
    - Agree to the terms and proceed through the setup.

## 3. Setting Up Your JavaScript Project in VS Code

1. **Open Visual Studio Code**:
    - Launch VS Code from your application menu.
    - create a folder in C drive and call it dev.
    - create a folder inside dev and call it Javascript 
    - click on file then open folder and open the folder dev in vs code

![](3.png)

![](5.png)

2. **Open a New Terminal Window**:
    - In VS Code, open a terminal by selecting `Terminal` → `New Terminal`.
   
3. **Initialize a New Node.js Project**:
    - In the terminal, execute:
      ```
      npm init -y
      ```
    - This creates a `package.json` file with default settings. `npm` is the Node Package Manager, `init` creates a new project, and `-y` accepts all default settings.

![](6.png)

4. **Create a JavaScript File**:
    - In VS Code’s file explorer, right-click and select `New File`.
    - Name the file `app.js` (the `.js` extension indicates it’s a JavaScript file).

5. **Add JavaScript Code**:
    - Open `app.js` and enter some JavaScript code. For example:
      ```javascript
      console.log('Hello, world!');
      ```
    - make sure you click on file then Auto save to always make sure code is saved 
   
![](Screenshot_(1).png)

6. **Run Your JavaScript File**:
    - In the terminal, type:
      ```
      node app.js
      ```
    - This command will run `app.js` and show the output in the terminal.

![](8.png)

## 4. Setting Up a Custom Script to Run Your Code

For ease of use, you can create a script to run your JavaScript file with a simple command:

1. **Edit `package.json`**:
    - Open `package.json` in the VS Code file explorer.

2. **Add a Start Script**:
    - Find the `"scripts"` section and add:
      ```json
      "scripts": {
        "start": "node app.js"
      }
      ```
    - Ensure that the syntax is correct with a comma if other scripts are present.

3. **Run Your Script**:
    - In the terminal, type:
      ```
      npm run start
      ```
    - This command will execute the `app.js` file using the custom script defined in `package.json`.

## Summary

By setting up Visual Studio Code and Node.js, you're equipped to write and execute JavaScript code locally. Follow these steps to create and manage your JavaScript projects efficiently. Enjoy coding!
