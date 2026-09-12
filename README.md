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
<img width="2549" height="570" alt="image" src="https://github.com/user-attachments/assets/51710d0c-41b8-4551-a8e1-84982e53d65b" />

if you see somthing like this click the last option (blank state) and move on 

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
## 🧠 Step 5: Connect a Model to Hermes Agent
With both tools installed, it's time to link them together using the 9Router Web UI and the Hermes CLI.
first open the terminal and write :
```
9router
```
to start the server .
then open a another terminal and run hermes model :
```
hermes model 
```
When prompted to pick a provider, select the option for your local network (localhost:20128) and press Enter.

<img width="1443" height="1350" alt="image" src="https://github.com/user-attachments/assets/1428ad16-7e8d-422b-8a92-878a163ad6f1" />

Access the 9Router Web Dashboard
Open your web browser and navigate to the 9Router Web UI. Log in using the default password (123456).
<img width="686" height="359" alt="image" src="https://github.com/user-attachments/assets/cbf2120a-9731-4fec-a95c-13e8a53dfd2f" />

Select Your Model
Browse the 9Router dashboard to find a model that fits your needs. You can choose from free tiers or paid options (my personal favorite is Gemini). Once you find it, grab its API details.

<img width="2559" height="820" alt="image" src="https://github.com/user-attachments/assets/41469b34-6a1d-4cc8-b9be-b2297e384409" />

Finalize and Launch
Go back to your second terminal, finish selecting your chosen model in the Hermes prompt, and start your agent. Run hermes and enjoy your automated AI workflow!
