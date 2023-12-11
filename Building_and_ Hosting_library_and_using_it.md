# Building and running a Python library locally
​
## Set Up Your Development Environment:
​
Ensure that Python is installed on your local machine.
Set up a virtual environment for your project to manage dependencies:
​
​
```bash
python -m venv myenv
source myenv/bin/activate  # On Windows use `myenv\Scripts\activate`
```
​
## Install Your Library Locally:
​
Use pip to install your library locally:
​
```bash
pip install .
```
If you want to install it in editable mode, which is useful for development, use:
​
```bash
pip install -e .
```
This allows you to make changes to the library and have those changes reflected without having to reinstall the library.
​
Run Your Library:
​
After installation, you can import your library in any Python script and use it just like you would with original presidio Python package.


# Build the Distribution Package:
  -Run the following command to create a distribution package for your library:
    ```bash
    python setup.py sdist
    ```

# Installation Guide
​
1. **Download the Distribution Package:**
   - Download the `.tar.gz` distribution package for the C4scale Presidio Analyzer library.
​
2. **Extract the Package:**
   - Use a tool like `tar` or a graphical archive manager to extract the contents of the downloaded `.tar.gz` file. (or winRAR on Windows)
​
     ```bash
     tar -xzvf C4scale_presidio_analyzer-<version>.tar.gz
     ```
​
3. **Navigate to the Package Directory:**
   - Change into the extracted directory:
​
     ```bash
     cd C4scale_presidio_analyzer-<version>
     ```
​
4. **Install the Library:**
   - Run the following command to install the library:
​
     ```bash
     python setup.py install
     ```
​
5. **Verify the Installation:**
   - Verify that the library is installed by running:
​
     ```bash
     pip show C4scale_presidio_analyzer
     ```
​
6. **Test the Library (Optional):**
   - If there are any provided tests, you can run them to ensure everything is working as expected:
​
     ```bash
     pytest
     ```
​
7. **Usage:**
   - You can now use the Presidio Analyzer library in your projects.



Hosting a Python library on GitHub is a straightforward and commonly used method. Here are the steps to host a Python library on GitHub:

### 1. Create a GitHub Repository:

1. **Create a GitHub Account:**
   - If you don't have a GitHub account, sign up at [github.com](https://github.com/).

2. **Create a New Repository:**
   - Click on the "+" sign in the upper right corner of the GitHub interface and choose "New repository."
   - Fill in the repository name, add a description, and choose the repository visibility (public or private).

3. **Initialize with a README (Optional):**
   - You can choose to initialize the repository with a README file.

4. **Create Repository:**
   - Click the "Create repository" button.

### 2. Push Your Python Library to GitHub:

1. **Push Your Code to GitHub:**
   - Push your Python library code to the GitHub repository using Git. Assuming you've initialized a Git repository locally:

   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/your-username/your-repository.git
   git push -u origin master
   ```

   Replace `your-username` and `your-repository` with your GitHub username and repository name.

### 3. Make Your Library Installable via `pip`:

1. **ensure a `setup.py` File:**
   - ensure a `setup.py` file in the root of your project to define metadata about your package.

2. **Tag a Release:**
   - Tag a release in your GitHub repository. This is usually done through the GitHub web interface. Go to the "Releases" section and click on "Draft a new release."

3. **Publish the Release:**
   - Publish the release, and GitHub will automatically generate a source distribution for your library.

### 4. Install the Library Using `pip`:

1. **Install the Library:**
   - On other machines, users can install your library using:

   ```bash
   pip install git+https://github.com/your-username/your-repository.git@v0.1
   ```
   
   ```bash
   pip install 'vcs+protocol://repo_url/#egg=pkg&subdirectory=pkg_dir'
   ```
   example:

   ```bash
   pip install 'git+https://github.com/kmr-hrsh/libraries_poc.git#egg=your-library1&subdirectory=subfolder1/'
   ```
   "subdirectory" component is used. Value of "subdirectory" component should be a path starting from root of the project to where setup.py is located. So if your repository layout is:

- pkg_dir/
  - setup.py  # setup.py for package ``pkg``
  - some_module.py
- other_dir/
  - some_file
- some_other_file

   Replace `your-username`, `your-repository`, and `v0.1` with your GitHub username, repository name, and the version tag you created.

There are a few ways to handle authentication when installing a Python library from a private GitHub repository:

### 1. Personal Access Token:

**Generate a Personal Access Token:**
1. Go to your GitHub account settings.
2. Navigate to "Developer settings" > "Personal access tokens."
3. Generate a new token with the "repo" scope.

**Install the Library:**
```bash
pip install git+https://<username>:<token>@github.com/your-username/your-private-repository.git@v0.1
```
Replace `<username>`, `<token>`, `your-username`, `your-private-repository`, and `v0.1` with your GitHub username, the personal access token, the name of your private repository, and the version tag you created.

### 2. SSH Key:

**Set Up SSH Key:**
1. Add your SSH key to your GitHub account.
2. Clone the repository using the SSH URL:
   ```bash
   git clone git@github.com:your-username/your-private-repository.git
   ```

**Install the Library:**
```bash
pip install git+git@github.com:your-username/your-private-repository.git@v0.1
```
Replace `your-username`, `your-private-repository`, and `v0.1` with your GitHub username, the name of your private repository, and the version tag you created.

### 3. Use a `.netrc` File:

**Create a `.netrc` File:**
1. Create a `.netrc` file in your home directory.
2. Add your GitHub credentials to the file:
   ```
   machine github.com
   login your-username
   password your-token
   ```

**Install the Library:**
```bash
pip install git+https://github.com/your-username/your-private-repository.git@v0.1
```
Replace `your-username`, `your-token`, `your-private-repository`, and `v0.1` with your GitHub username, the personal access token, the name of your private repository, and the version tag you created.

Choose the authentication method that suits your preferences and security requirements. Note that personal access tokens are a common and recommended approach for private repositories, providing a balance between security and ease of use.
