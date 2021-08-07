# Developer Guidelines

## How to contribute

Contributions to `babamul` are made through [GitHub Pull Requests](https://help.github.com/en/github/collaborating-with-issues-and-pull-requests/about-pull-requests), a set of proposed commits (or patches).

To prepare, you should:

- Create your own fork the [babamul repository](https://github.com/babamul/babamul) by clicking the "fork" button.

- [Set up SSH authentication with GitHub](https://help.github.com/en/github/authenticating-to-github/connecting-to-github-with-ssh).

- Clone (download) your copy of the repository, and set up a remote called `upstream` that points to the main `babamul` repository.

  ```shell script
  git clone git@github.com:<yourname>/babamul && cd babamul
  git remote add upstream git@github.com:babamul/babamul
  ```

Then, for each feature you wish to contribute, create a pull request:

1. Download the latest version of `babamul`, and create a new branch for your work.

   Here, let's say we want to contribute some documentation fixes; we'll call our branch `rewrite-contributor-guide`.

   ```shell script
   git checkout master
   git pull upstream master
   git checkout -b rewrite-contributor-guide
   ```

2. Make modifications to `babamul` and commit your changes using `git add` and `git commit`.
Each commit message should consist of a summary line and a longer description, e.g.:

   ```text
   Rewrite the contributor guide

   While reading through the contributor guide, I noticed several places
   in which instructions were out of order. I therefore reorganized all
   sections to follow logically, and fixed several grammar mistakes along
   the way.
   ```

3. When ready, push your branch to GitHub:

   ```shell script
   git push origin rewrite-contributor-guide
   ```

   Once the branch is uploaded, GitHub should print a URL for turning your branch into a pull request.
   Open that URL in your browser, write an informative title and description for your pull request, and submit it.

4. The team will now review your contribution, and suggest changes.
*To simplify review, please limit pull requests to one logical set of changes.*
To incorporate changes recommended by the reviewers, commit edits to your branch, and push to the branch again
(there is no need to re-create the pull request, it will automatically track modifications to your branch).

5. Sometimes, while you were working on your feature, the `master` branch is updated with new commits, potentially
resulting in conflicts with your feature branch. Please merge the upstream/master branch into your branch:

    ```shell script
    git merge rewrite-contributor-guide upstream/master
    ```
Developers may merge `master` into their branch as many times as they want/need to.

6. Once the pull request has been reviewed and approved by at least two team members, it will be merged into `babamul`.

## Setting up your environment

We use `black` to format the code and `flake8` to verify that code complies with [PEP8](https://www.python.org/dev/peps/pep-0008/).
Please install our pre-commit hook as follows:

    ```shell script
    pip install pre-commit
    pre-commit install
    ```

This will check your changes before each commit to ensure that they
conform with our code style standards. We use black to reformat Python
code.

The pre-commit hook will lint *changes* made to the source.

---

You may want to create/activate a virtual environment, for example:

```bash
python -m venv babamul-env
source babamul-env/bin/activate
```

Make sure the requirements to run it are met, e.g.:

```bash
pip install -r requirements.txt
```
