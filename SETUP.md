# Mkdocs Setup

The long-term objective is to extend and maintain this site with AI-driven content generation and automation tooling. For now, we start with traditional setup and configuration as follows.

---

## 1. Create dev container

1. Open cloned repository in Visual Studio Code (VS Code).
1. Click green button (bottom left corner) to open the command palette.
1. Select "Dev Containers: Create Dev Container Configuration File".
1. Choose "Python 3" as the base image.
1. Confirm to generate base dev container configuration files.

You should now have a `.devcontainer` folder in your project root.

1. Open VS Code Extensions in sidebar.
1. Search for Microsoft Python and Jupyter extensions
1. In each case, right click and `add to dev container
1. Your `devcontainer.json` should be updated accordingly.
1. Your VS Code extension setup is ready.

Create a `requirements.txt` file in the root of your project.

1. Set `postCreateCommand` to install dependencies from this.
1. Add `mkdocs-material` to `requirements.txt` to start
1. Your Python environment setup is ready.

**Click the green button (bottom left corner) - select "Reopen in Container**. 

1. VS Code editor will show a message that dev container is being built. 
1. When done, green button shows "Dev Container: Python 3" 
1. The VS Code terminal will now be active and ready to use.

<br/>


## 2. Setup Mkdocs site

1. Run this command to verify `mkdocs` was installed. 

   ```bash
   mkdocs --version
   ```
   You should see

   ```bash
    mkdocs, version 1.6.1 from `/home/vscode...`
   ```

2. Create a new Mkdocs site with the following command:

   ```bash
   mkdocs new .
   ```

   You shoud see:
   
   ```bash  
    INFO    -  Writing config file: ./mkdocs.yml
    INFO    -  Writing initial docs: ./docs/index.md
   ````

## 3. Preview Mkdocs site

1. Run the following command to start the Mkdocs development server:

   ```bash
   mkdocs serve
   ```

   You should see output similar to:

   ```bash
    INFO    -  Building documentation...
    INFO    -  Cleaning site directory
    INFO    -  Documentation built in 0.07 seconds
    INFO    -  Watching paths for changes: 'docs', 'mkdocs.yml'
    INFO    -  Serving on http://127.0.0.1:8000/
    ```

1. Click the pop-up dialog option to open in browser. You should see basic mkdocs site with a single page. This reflects the configuration in `mkdocs.yml` and the initial content in `docs/index.md`.

## 4. Update Mkdocs configuration

1. Update the `mkdocs.yml` file to customize site. _I simply reused the config from a different project and customized it._

## 5. Deploy to GitHub Pages

**First, I prime GitHub Pages with a manual deploy**:

1. Run this command from the VS Code terminal:

    ```bash
    mkdocs gh-deploy --force
    ```
1. Once done, go to the repository settings and enable GitHub Pages for the `gh-pages` branch.
1. You should now be able to access the site at `https://ai-for-autodidacts.github.io/azure-ai-foundry/`.

**Next, I setup automated GitHub Actions**:

1. Create `.github/workflows` if not already present.
1. Create a new file `mkdocs-ghdeploy.yml` in this folder.
1. Add content from [this mkdocs guidance](https://squidfunk.github.io/mkdocs-material/publishing-your-site/?h=github#with-github-actions) to the file.
1. Commit these changes to the repository to activate.

**Now, when you push updates to the `main` branch, the site will be automatically built and deployed to GitHub Pages.**
