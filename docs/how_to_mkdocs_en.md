# Instruction: Publishing notes as a website (MkDocs + GitHub Pages)

This document is a guide that will allow you to independently build and publish a modern documentation website – exactly like the one you are seeing now. We will use the **MkDocs** framework with the **Material** theme and free **GitHub Pages** hosting to quickly and professionally share math notes on the internet.

## Step 1: Initialize the Repository (VS Code)

We will use the built-in features of Visual Studio Code to quickly publish the project.

1.  Open **Visual Studio Code** and select `File > Open Folder...`, pointing to a new, empty directory on your disk.
2.  Create any file in this folder, for example, an empty file named `README.md` (Git requires at least one file to create a repository).
3.  Save the file.
4.  Go to the **Source Control** tab (the graph/tree icon on the left sidebar).
5.  Click the blue **Publish to GitHub** button.
6.  Choose the option to publish as a **Public repository**.

*After this operation, your folder is already connected to GitHub.*

## Step 2: Automatic configuration (AI Agent)

Now we will ask the AI Agent in Visual Studio Code to prepare the Python environment and the MkDocs structure.

Copy the following **Prompt** and paste it into the chat with the Agent:

> **Prompt for the Agent:**
>
> "You are an expert in technical documentation in Python. Please prepare the environment for MkDocs in the current folder. Perform the following steps:
>
> 1. Create a Python virtual environment (`.venv`) and provide the command to activate it.
> 2. Create a `.gitignore` file to exclude temporary files from the repository. Be sure to add:
>    - `.venv/` (virtual environment),
>    - `site/` (built site folder),
>    - `__pycache__/`.
> 3. Install the following packages in this environment: `mkdocs` and `mkdocs-material`.
> 4. Generate the structure of a new project in the main directory (`mkdocs new .`).
> 5. Overwrite the `mkdocs.yml` configuration file, setting `site_name` to 'Math Notes' and changing the theme (`theme`) to `name: material`.
>
> Do not start the server, just prepare the files."

*Remember to enter the environment activation command (the one provided by the Agent) in the terminal after the Agent has completed the instructions.*

## Step 3: Publishing the site (Deployment)

When the project is preliminarily ready, we use a single command to build the site and send it to the server.

Enter in the terminal:

```bash
mkdocs gh-deploy
```

## Step 4: The final effect

You don't have to guess your site's address or construct it manually. After successfully executing the `mkdocs gh-deploy` command, look at the logs in the terminal.

At the very end, a direct link to your published page will appear. Just click it (in VS Code, usually with the `Ctrl` or `Cmd` key pressed) to see your notes online.

## Step 5: How to work on a daily basis? (Local Development)

You don't have to send the site to the GitHub server (`gh-deploy`) every time you fix a typo or add a formula. More efficient work involves previewing changes locally on your computer.

**Current work instructions:**

1.  Enter in the VS Code terminal:
    ```bash
    mkdocs serve
    ```
2.  Open the address that appears in your browser (usually `http://127.0.0.1:8000/`).
3.  Edit the `.md` files in the `docs` folder. Every time you save a file (`Ctrl+S`), the page in the browser will refresh automatically.
4.  Only when you finish your work and are satisfied with the result, stop the server (`Ctrl+C`) and send the changes "to the world" with the command from step 3:
    ```bash
    mkdocs gh-deploy
    ```

## Step 6: Adding content and configuring mathematics

As before, we create files with notes (Markdown) in the `docs` folder. For a new note to be visible in the site's sidebar, it must be added to the `mkdocs.yml` configuration file. In addition, we need to make sure that MkDocs can render mathematical formulas (LaTeX).

Let's use the Agent to create a sample note, add it to the navigation, and configure math support.

Copy the following **Prompt** and paste it to the Agent:

> **Prompt for the Agent (Adding content and LaTeX):**
>
> "Please expand the project with a new note and mathematics configuration.
>
> 1.  Create a file named `derivatives.md` in the `docs` folder. Write a short note in it about function derivatives, including a definition and an example formula formatted in LaTeX (use dollar signs).
> 2.  Update the `mkdocs.yml` file by adding this file to the navigation section (`nav`) under the name 'Derivatives'.
> 3.  **Very important:** Modify `mkdocs.yml` to add full support for rendering mathematical formulas. Configure the `pymdownx.arithmatex` extension and add the necessary `extra_javascript` and `extra_css` entries (for the MathJax or KaTeX library) so that the formulas on the page display correctly, not as raw code."

**What to do after the Agent completes the task?**

1.  Start the local server: `mkdocs serve`.
2.  Check in the browser if the new "Derivatives" tab has appeared and if the mathematical formulas look nice (are not raw text with dollar signs).
3.  If everything works, stop the server and publish the changes: `mkdocs gh-deploy`.
4.  Open the link from the logs and check the public version.

## Step 7: Interactive Simulations (HTML + AI)

Your documentation does not have to be limited to static text. Modern AI chats (such as **Gemini, Claude, or ChatGPT**) can generate working physics and mathematical simulations in HTML/JavaScript. You can easily "embed" them into your notes page.

**Simulation creation process:**

1.  **Code generation:** Go to the selected AI chat (e.g., Gemini or Claude) and ask for a simulation to be generated.

      * *Example prompt for an external AI:*
        > "Write me a simulation of a projectile motion (or a visualization of matrix addition) as a single HTML file with embedded CSS and JavaScript. I want the user to be able to change parameters with sliders, and the result to be visible on a chart/animation."

2.  **Saving the file:**

      * Copy the received HTML code.
      * In the `docs` folder (where you have your `.md` files), create a new file, e.g., `projectile_motion.html` and paste the code into it.

3.  **Integration with navigation:**

      * HTML files can be added to the site menu in exactly the same way as Markdown files.
      * Ask the Agent in VS Code to add this file to the navigation.

Copy the following **Prompt** and paste it to the Agent in VS Code:

> **Prompt for the Agent (HTML Integration):**
>
> "In the `docs` folder, I created an HTML file with a simulation. Please update the `mkdocs.yml` file:
>
> 1.  Find the `nav` section.
> 2.  Add a new item to it called 'Simulation', which will point to this HTML file in the `docs` folder.
> 3.  Make sure that the structure of the configuration file remains correct."

**Verification:**
Run `mkdocs serve`. You should see a new "Simulation" item in the menu. After clicking it, your interactive application created by AI will open. When you are satisfied, push the changes to the server (`mkdocs gh-deploy`).