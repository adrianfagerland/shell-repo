# ReLU-NTNU Repository Template

## How to create a repo like this

1. With poetry installed (`pip install poetry`), and in the folder where you wish to store your project, create a new project with:

```bash
poetry new [project-name]
cd [project-name] # or potentially `code [project-name]` if using vscode
```

2. Install `ruff` to the dev group. This will use ruff for the development of the project, but not include it in the final package.:

```bash
poetry add ruff pre-commit --group dev
```

3. Copy the `.pre-commit-config.yaml` and `.gitignore` file from this repo to the root of your project. In the future, remember to actively edit the `.gitignore` file if the need arises in order to prevent repo clutter.

4. Create a new repo in the ReLU-NTNU organisation on GitHub. You do not need to add a license, `.gitignore` or `README.md`. Then, copy the URL of the repo which should appear after creating the repo. This should look something like `https://github.com/ReLU-NTNU/solution-seeker.git`. Then, set up git for your project with these commands:

```bash
git init
git remote add origin [url]
git branch -M main
git add .
git commit -m "initial commit"
git push -u origin main
```

5. Lastly, run this to install the pre-commit hooks:

```bash
poetry shell
pre-commit install
```

## ! Important notes

- When a new developer clones the repository, they will need to do a few things. Assuming `python`, `pip` and `poetry`, they need to run:

```bash
poetry install # this installs the dependencies and creates a virtual environment
poetry shell # this activates the virtual environment in the terminal
pre-commit install # this installs the pre-commit hooks
```

- `pre-commit` will now run every time the user tries to commit changes to the repository. If the pre-commit hooks fail, the user will not be able to commit the changes. This is to maintain main branch protection and code quality. Tests hooks could also be added here, but that is not included in this repo. The pre-commit hooks should fix the files it found an error with, so if the developer stages the file again with for example `git add [file-name]`, the pre-commit hooks should pass.

- It is recommended to get a basic understanding of how to use [`poetry`](https://python-poetry.org/docs/basic-usage/). Especially, you have to add dependencies in the right way using `poetry add [package-name]` and `poetry add [package-name] --dev` for development dependencies.

- Remember to create a `scripts/` and `notebooks/` folder when you need to store scripts and notebooks.
