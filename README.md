# 🚀 Deploying Hermes Agent with 9Router on Windows

This guide provides a clean, step-by-step walkthrough for installing Node.js, setting up 9Router, installing Hermes Agent, and connecting them together on a Windows machine.

---

## ⚙️ Step 1: Install Node.js

9Router is a Node package, so you need to install Node.js first.

1. Go to the [official Node.js website](https://nodejs.org/) and download the standard Windows Installer (.msi).
2. Run the installer and click "Next" through the default setup prompts. 
3. Open a new **PowerShell** window and verify the installation by typing:
   ```powershell
   node -v
   npm -v

   (If both commands return version numbers, you are ready for the next step).

## 🛠️ Step 2: Install 9Router
Now that Node.js is on your system, you can install 9Router directly from your terminal.

In your PowerShell window, run the following command to install 9Router globally:

 ```
PowerShell
  npm install -g 9router 
  ```

Once installed, start the 9Router server on its default port:
```
PowerShell
  9router --port 20128
```
(Note: Leave this terminal window open so 9Router continues to run in the background).

## 🤖 Step 3: Install Hermes Agent
Hermes Agent has a native installation script for Windows.

Open a new, separate PowerShell window (keep your 9Router terminal running).

Run the official Hermes Agent installation command:

```
PowerShell
    iex (irm [https://hermes-agent.nousresearch.com/install.ps1](https://hermes-agent.nousresearch.com/install.ps1))
```
## 🔗 Step 4: Connect Hermes Agent to 9Router
Finally, you need to tell Hermes Agent to route its requests through your local 9Router instance instead of the public internet.

In the same PowerShell window where you installed Hermes, set the base URL environment variable to point to 9Router's local address:
```
PowerShell
 $env:OPENAI_API_BASE="http://localhost:20128/v1"
```
Now, simply start your agent:
```
PowerShell
 hermes
```
Your Hermes Agent is now successfully running and routing all its traffic directly through your local 9Router instance!
