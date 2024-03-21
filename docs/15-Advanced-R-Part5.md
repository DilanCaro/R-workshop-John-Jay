# (Optional) Part V: Version Control and Collaboration (10 minutes) {-}
## Using Git and GitHub for version control and collaboration in R projects {-}

Git is a distributed version control system that helps track changes in source code during software development. GitHub is a cloud-based hosting service that lets you manage Git repositories.

Integrating Git with R:
1. Install Git and set up a GitHub account.
2. Configure Git with your username and email.
    - Use Git Bash or the terminal: 
      git config --global user.name "Your Name"
      git config --global user.email "your.email@example.com"

3. Initialize a Git repository in an R project:
    - In RStudio, start a new project and select the option to create a Git repository.

4. Basic Git commands:
    - git init: Initialize a new Git repository.
    - git status: Check the status of changes.
    - git add: Add files to the staging area.
    - git commit: Commit changes to the repository.
    - git push: Push changes to a remote repository like GitHub.
    - git pull: Pull updates from a remote repository.

 5. Collaborating with GitHub:
    - Fork and clone repositories.
    - Create branches for features or fixes.
    - Use pull requests for code reviews.
    - Merge changes to the main branch.

*Exercise*:

 1. Create a new R project with a Git repository.
 2. Make changes in your project, commit them, and push them to a GitHub repository.
 3. Collaborate with a colleague or friend by having them fork your repository and submit a pull request.
