# Team Software Project Starter Template - Flask

This example shows how to implement a basic app using:

- [Flask](https://flask.palletsprojects.com/en/3.0.x/) 
- [Prisma Client](https://prisma-client-py.readthedocs.io/en/stable/) as the ORM
- A SQLite database file with some initial dummy data which you can find at [`./prisma/dev.db`](./prisma/dev.db)
- [Bootstrap](https://getbootstrap.com/) for basic CSS Styling.
- [Pytest](https://docs.pytest.org/en/7.4.x/) for unit testing
- [pylint](https://pypi.org/project/pylint/) to statically analyze your code and find problems
- [black: The Uncompromising Code Formatter](https://pypi.org/project/black/) to format your code

It is intended to serve as a starting point for your Team Software Project course if you choose to use ExpressJS. It
provides examples for performing basic tasks with different types of endpoints (GET, POST, etc.)

## Getting started

> Note: You may consider using pyenv to create a separate python environment that is configured specifically for this
> app.  Please see the section below with the general steps for getting up and running with pyenv if you want to use
> this path.

### 1. Download example and install dependencies

Clone this repository:

```bash
git clone git@github.com:kiboschool/tsp-flask-starter-template.git

cd tsp-flask-starter-template

```

Setup and activate your virtual environment:

`python3 -m venv .venv`

`source .venv/bin/activate`

Install dependencies:

```bash
pip3 install -r requirements.txt
```

### 2. Create and seed the database

Run the following command to create your SQLite database file. This also creates the `User` and `Post` tables that are
defined in [`prisma/schema.prisma`](./prisma/schema.prisma):

```bash
prisma db push
```

Seed the database by running the `./prisma/seed.py` file

```bash
python3 ./prisma/seed.py
```

### 3. Interacting with the Starter Template

```bash
flask run
```

If you encounter this error:
```
Traceback (most recent call last):
  File "/opt/homebrew/lib/python3.10/site-packages/flask/cli.py", line 219, in locate_app
    __import__(module_name)
  File "/Users/msaudi/kibo/tsp-flask-starter-template/app/__init__.py", line 3, in <module>
    from flask_jwt_extended import JWTManager
ModuleNotFoundError: No module named 'flask_jwt_extended'
```
It means your virtual environment uses a different python version than the one in the environment itself. To fix this, do the following steps:

1. Open this file `.venv/bin/activate` using your favorite text editor
2. Add this line to the end of the file `export PYTHONPATH="./.venv/bin/python3"`
3. Save and close the file
4. Source the file in the terminal using this command `source .venv/bin/activate`
5. Run your flask project `flask run`

### Additional Commands

**pylint configuration is stored in the `.pylintrc` file.**

Check if the formatting matches pylint's rules by running

``` bash
pylint app
```

Format your code with Black using this command:

``` bash
black app
```

Run unit tests with this command:

```bash
pytest tests
```

### Deploying To Render

You can deploy this application to Render using the following steps:

1. Once you have pushed the remote to a GitHub repository, go to render.com and select 'Get Started For Free'.
2. Log in using your GitHub account.
3. Select the option to deploy a new Web Service
4. Choose the option to 'Build and deploy from a Git repository'.  If you don't see your repository in the list, select
   the option to "Configure account" on the right-hand side of the screen.  You can then select which repo you would
   like to link.
5. Click on 'Connect' to the right of the correct repository.
6. Choose a name and region of your choice.  
7. For the 'Start Command' enter `flask run`.
8. Select the Free Plan option.
9. Click 'Create Web Service'.

## Using pyenv

1. **Install pyenv:** If you haven't already installed `pyenv`, you can do so by following the instructions on the [pyenv GitHub page](https://github.com/pyenv/pyenv#installation). 
   
2. **Install Python Version:** Use `pyenv` to install the specific version of Python that you want for your Flask application. For example:
   ```bash
   pyenv install 3.11.6
   ```

3. **Set the Local Python Version:** Navigate to your Flask application directory and set the local Python version to the one you installed. This ensures that your Flask application uses the correct Python version.
   ```bash
   cd path/to/your/flask/app
   pyenv local 3.11.6
   ```

4. **Create a Virtual Environment (Optional):** While `pyenv` manages Python versions, it's still a good practice to use a virtual environment for your Flask application to manage dependencies. You can use `pyenv-virtualenv`, an extension for `pyenv`, to create a virtual environment. Install `pyenv-virtualenv` if you haven't, and then create a new environment:
   ```bash
   pyenv virtualenv 3.11.6 my-flask-env
   pyenv local my-flask-env
   ```

Remember, every time you work on your Flask application, you should navigate to your application directory first. `pyenv` will automatically switch to the correct Python version as set by the `pyenv local` command.
