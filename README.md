<header>

<!--
  <<< Author notes: Course header >>>
  Read <https://skills.github.com/quickstart> for more information about how to build courses using this template.
  Include a 1280×640 image, course name in sentence case, and a concise description in emphasis.
  In your repository settings: enable template repository, add your 1280×640 social image, auto delete head branches.
  Next to "About", add description & tags; disable releases, packages, & environments.
  Add your open source license, GitHub uses the MIT license.
-->

# Remove commit history

Accidental commits can be tricky to remove with Git. In this GitHub Skills course, you'll use BFG Repo-Cleaner to change the history of a Git repository. You can apply what you learn in this course to fully remove sensitive material from your own repository.

</header>

<!--
  <<< Author notes: Step 2 >>>
  Start this step by acknowledging the previous step.
  Define terms and link to docs.github.com.
-->

## Step 2: Removing a file from Git history using BFG Repo-Cleaner

_You removed `.env` from the repository's root directory! :tada:_

Now that we've deleted the file, people that browse the repository on GitHub.com or anyone looking at just the head commit won't see the file. However, due to Git's nature, the file is still present in the history. In this step, we'll work on removing the file from the repository history.

**What is a _head commit_**? In Git, HEAD points to a branch or a commit. When we say [head commit](https://docs.github.com/en/get-started/quickstart/github-glossary#head), we usually mean the most recent commit in the repository's history.

There are multiple tools available for removing Git history, we'll use BFG Repo-Cleaner in this step. You can find additional documentation on [Using the BFG in GitHub Docs](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#using-the-bfg).

**What is _BFG Repo-Cleaner_**? BFG Repo-Cleaner is software that can help you search through and alter repository history. Git can natively do this using [`git filter-repo`](https://docs.github.com/en/authentication/keeping-your-account-and-data-secure/removing-sensitive-data-from-a-repository#using-git-filter-repo), but it can be more complex.

### :keyboard: Activity: Use BFG Repo-Cleaner to remove the `.env` file

1. Update the local copy of your repository to ensure you have the most recent version of the course files.
   ```shell
   git pull
   ```
2. Install BFG Repo-Cleaner on your machine. You can follow the [instructions on the web site](https://rtyley.github.io/bfg-repo-cleaner/) to do so or you can use a package manager for your operating system.
3. Confirm the `.env` file is removed from the root directory. The command should return empty.
   ```shell
   find . -name ".env"
   ```
4. Search for .env in the repository's history. The command should return at least 2 commits: the addition of `.env` when you copied this template repository, and the removal of `.env`.
   ```shell
   git log --stat --all -- .env
   ```
5. Use BFG Repo-Cleaner to delete all references to `.env` that exist in the repository.
   ```shell
   bfg --delete-files .env
   ```
6. The tool will run and make some suggestions about some follow-up commands. Run those to get your local repository cleaned up.
7. Repeat the search for `.env` in the repository's history. This time, the command should return empty.
   ```shell
   git log --stat --all -- .env
   ```
8. Push your changes to GitHub. Note we're using the `--force` argument in this step since we're altering Git history.
   ```shell
   git push --force
   ```
9. Wait about 20 seconds then refresh this page (the one you're following instructions from). [GitHub Actions](https://docs.github.com/en/actions) will automatically update to the next step.

<footer>

<!--
  <<< Author notes: Footer >>>
  Add a link to get support, GitHub status page, code of conduct, license link.
-->

---

Get help: [Post in our discussion board](https://github.com/orgs/skills/discussions/categories/change-commit-history) &bull; [Review the GitHub status page](https://www.githubstatus.com/)

&copy; 2024 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)

</footer>
