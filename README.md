# ReLU-NTNU Repository Template

## How to create a repo like this

1. We use [`uv`](https://docs.astral.sh/uv/getting-started/installation/#standalone-installer), install it if you do not yet have it. Run these commands:

```bash
mkdir [project-name] # this will make a folder for your project
cd [project-name] # this will go into the folder. If using VSCode, you can open the folder in VSCode with `code [project-name]`
uv init --package # this creates a package with the name of the folder ([project-name])
```

2. Install `ruff`, `pre-commit` and `ty` as dev dependencies in the `pyproject.toml` file. This is done by running:

```bash
uv add ruff pre-commit ty --dev
```

3. Copy the `.pre-commit-config.yaml` and `.gitignore` file from this repo to the root of your project, overwriting the `.gitignore` file generated with `uv init --package`. In the future, remember to actively edit the `.gitignore` file if the need arises in order to prevent repo clutter. Then you can run:

```bash
uv run pre-commit install
```

4. Create a new repo in the ReLU-NTNU organisation on GitHub. You do not need to add a license, `.gitignore`, or `README.md`. Then, copy the URL of the repo which should appear after creating the repo. This should look something like `https://github.com/ReLU-NTNU/solution-seeker.git`. Then, set up git for your project with these commands:

```bash
git init
git remote add origin [url]
git branch -M main
git add .
git commit -m "initial commit"
git push -u origin main
```

## ! Important notes

- When a new developer clones the repository, they will need to do a few things. Assuming they are using `uv`:

```bash
uv sync # this creates a virtual environment and installs the dependencies
source .venv/bin/activate # this activates the virtual environment in the terminal. If using VSCode, you should also select the virtual environment in the bottom left corner, or using the "Python: Select Interpreter" VSCode command
uv run pre-commit install # this installs the pre-commit hooks
```

- `pre-commit` will now run every time the user tries to commit changes to the repository. If the pre-commit hooks fail, the user will not be able to commit the changes. This is to maintain main branch protection and code quality. Tests hooks could also be added here, but that is not included in this repo. The pre-commit hooks should fix the files it found an error with, so if the developer stages the file again with for example `git add [file-name]`, the pre-commit hooks should pass.

- It is recommended to get a basic understanding of how to use [`uv`](https://docs.astral.sh/uv/). Especially, you have to add dependencies in the right way using `uv add {package-name}` and `uv add {package-name} --dev` for development dependencies.

- Remember to create a `scripts/` and `notebooks/` folder when you need to store scripts and notebooks.

- Using the `--package` flag when creating a new project with `uv` will create a function in `src/{package-name}/__init__.py` that can be run with `uv run {package-name}` because of the reference created in `pyproject.toml` under `[project.scripts]`. This is useful for running the application you are developing.
