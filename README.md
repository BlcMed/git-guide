# Practical Guide to Git & GitHub Basics

## Introduction to Git and GitHub

1. **What is Git?**  
   Git is a version control system that helps manage changes to files and code. It enables multiple people to work on a project simultaneously, tracks changes, and allows you to revert to previous versions if needed.

2. **What is GitHub?**  
   GitHub is an online platform for hosting and collaborating on Git repositories. It allows users to share projects, track contributions, and manage collaborative workflows.

3. **Setting Up Git and GitHub**
   - **Create a GitHub account** at [github.com](https://github.com/).
   - **Install Git**: Download and install Git from [git-scm.com](https://git-scm.com/).
   - **Set up Git username and email** (important for tracking contributions):
     ```bash
     git config --global user.name "Your Name"
     git config --global user.email "your.email@example.com"
     ```
   
   **Important Note for Windows Users:**
   If Git is still not being detected after installation (i.e., running git in the terminal results in an error or the command is not recognized), you may need to manually add Git's binary directory to your system’s PATH. Here’s how:

    - **Locate the Git Binary Path:**
    Typically, Git is installed in C:\Program Files\Git\bin or C:\Program Files (x86)\Git\bin on Windows.

    - **Add Git to PATH:**
        - Right-click on This PC (or Computer) and select Properties.
        - Click on Advanced system settings on the left.
        - Under System Properties, click on the Environment Variables button.
        - In the System variables section, find and select the Path variable, then click Edit.
        - In the Edit window, click New and add the path to the bin directory (e.g., C:\Program Files\Git\bin).
        - Click OK to save the changes and restart your terminal.

After this, Git should be recognized in your terminal, and you can continue with the Git setup.
---

## Use Case: Basic Collaboration Between Two People

### **Starting Setup: Creating and Cloning the Repository**

1. **Create a New Repository on GitHub (Person A)**  
   - *Person A* logs into GitHub, navigates to the main GitHub page, and clicks on **New** or **+ New Repository**.

     ![](assets/0-home-page.png)
   - In the repository creation page:
     - **Repository Name**: Enter a name, e.g., `dummy-repo`.
     - **Description**: Optionally, add a short description.
     - **Visibility**: Choose **Public** or **Private**.
     - Select **Initialize this repository with a README** to create a starter file.
   - Click **Create repository**.

     ![](assets/1-new-repo.png)

> **Note**: A README is usually the first thing a visitor sees when exploring your repository. It typically provides essential information such as:
> - What the project does
> - Why the project is useful
> - How users can get started with the project
> - Where users can get help
> - Who maintains and contributes to the project

   ![](assets/2-readme.png)

2. **Invite Collaborators (Person A)**
   - After creating the repository, *Person A* goes to **Settings** > **Collaborators and teams**.

     ![](assets/3-settings.png) ![](assets/4-settings-colab.png)
   - Add *Person B’s* GitHub username or email to give them access to the repository.

     ![](assets/5-colab.png)

3. **Accept Invitation (Person B)**
   - *Person B* accepts the invitation to join the repository.

     ![](assets/6-pending.png)

4. **Clone the Repository (Both People)**

   - For better organization, it's a good idea to create a dedicated folder for your projects. For example, you can create a folder named projects to store all your repositories. Once you've created the folder, you can proceed with cloning the repository inside it.
   
   - You can create the folder and navigate into it using the following commands:
   ``` bash
   mkdir projects  # Create a 'projects' folder
   cd projects     # Change directory into the 'projects' folder
   ```
   
   Once you're inside the projects folder, you can proceed with cloning the repository.

   - After receiving access, *Person B* can clone the repository.
   - Both *Person A* and *Person B* copy the SSH or HTTPS link from the repository page and run this command in their terminal:
     ```bash
     git clone https://github.com/username/dummy-repo.git
     ```

     ![](assets/7-clone-repo.png) ![](assets/8-cloning.png)
   - Now, each person has a local copy of the repository. They can open the folder in VS Code. 
     ![](assets/9-cloned.png)

   Once the repository is cloned, you will see that the `dummy-repo` folder is inside the `projects` folder. To start working with the repository, you need to either change into the project directory   using the `cd` command or open the folder directly in VS Code.
   
   - To navigate to the cloned repository folder, use:
   
   ```bash
   cd dummy-repo
   ```
   
   Alternatively, you can open the folder directly in VS Code:
   
   ```bash
   code .
   ```

   - Check the status with:
     ```bash
     git status
     ```
     ![](assets/10-status-after-cloning.png)

---

### **Step 1: Person A Modifies and Pushes Changes**

1. **Edit a File**  
   - *Person A* opens `README.md` (or any other file) and adds a new line, such as:
     ```plaintext
     # dummy-repo
     
     This is a demo of a basic Git workflow for collaboration.
     ```

     ![](assets/11-modify-readme.png)

    - **Important Note:**
    Make sure to save your changes before moving on! You can either manually save the file by pressing Ctrl + S (Windows/Linux) or Cmd + S (Mac), or you can enable auto-save in VS Code to automatically save changes as you make them. To enable auto-save in VS Code:

   - Go to File > Auto Save in the top menu.

   - Alternatively, open the Command Palette (Ctrl + Shift + P or Cmd + Shift + P on Mac), search for Auto Save, and choose your preferred auto-save option.

    Saving the file (or enabling auto-save) is important so that Git can detect your changes when you run commands like git status and git add.



3. **Stage the File**  
   - In the terminal, *Person A* stages the modified file to prepare it for committing:
     ```bash
     git add README.md
     ```
     ![](assets/14-staging-changes.png)

4. **Commit the Change**  
   - *Person A* commits the change with a descriptive message:
     ```bash
     git commit -m "Add project description to README"
     ```

     ![](assets/16-status-post-commit.png)

5. **Push to GitHub**  
   - *Person A* pushes the change to GitHub:
     ```bash
     git push origin main
     ```

     ![](assets/17-commit-changes.png)

   - Check the logs:
     ```bash
     git log
     ```

     ![](assets/19-log.png)

---

### **Step 2: Person B Pulls the Update and Adds Changes**

1. **Check Status after Person A's Changes**  
   - *Person B* can check the status of their repository to see if it’s up-to-date or if there are any changes pending a pull.
   
     ![](assets/20.jpeg)

2. **Pull Latest Changes**  
   - *Person B* updates their local repository to include *Person A's* changes by running:
     ```bash
     git pull origin main
     ```
   
     ![](assets/21.jpeg)  
     ![](assets/22.jpeg)

3. **Verify the Changes**  
   - *Person B* opens `README.md` locally to confirm that the new project description from *Person A* is present.

4. **Add New Changes (Person B)**  
   - *Person B* adds a new sample Python file to the project. After adding the file, they can check the status to see the new file as untracked.

     ![](assets/23.jpeg)  
     ![](assets/24.jpeg)

5. **Stage Changes**  
   - *Person B* stages the new file to prepare it for committing. They can confirm the status again to ensure the file is staged.

     ![](assets/25.jpeg)

6. **Commit Changes**  
   - *Person B* commits the newly added file with a descriptive message and checks the status to confirm the commit.

     ![](assets/26.jpeg)

7. **Push the Changes to GitHub**  
   - Finally, *Person B* pushes the new commit to the remote repository on GitHub.

     ![](assets/27.jpeg)

---

## Basic Git Cheat Sheet

### **Basic Commands**

1. **Create a New Repository Locally**
   ```bash
   git init
   ```

2. **Clone an Existing Repository**
   ```bash
   git clone <repository-url>
   ```

---

### **Making Changes**

1. **Check Repository Status**  
   Shows any changes in files that are staged, unstaged, or untracked.
   ```bash
   git status
   ```

2. **Stage Changes**  
   Adds specific files to the staging area.
   ```bash
   git add <file>
   ```
   Add all changes:
   ```bash
   git add .
   ```

3. **Commit Changes**  
   Records staged changes with a descriptive message.
   ```bash
   git commit -m "Your commit message"
   ```

4. **View Commit History**  
   Lists past commits.
   ```bash
   git log
   ```

---

### **Working with Remote Repositories (e.g., GitHub)**

1. **Push Changes to Remote Repository**  
   ```bash
   git push origin <branch-name>
   ```

2. **Pull Changes from Remote Repository**  
   ```bash
   git pull origin <branch-name>
   ```


---

### **Undoing Changes**

1. **Unstage a File**  
   ```bash
   git restore --staged <file>
   ```

2. **Discard Changes in a File**  
   ```bash
   git restore <file>
   ```

3. **Undo the Last Commit**  
   ```bash
   git reset --soft HEAD~1
   ```

4. **Reset to a Previous Commit**  
   Warning: This permanently deletes commits after the specified one.
   ```bash
   git reset --hard <commit-id>
   ```

---

### **Summary of Basic Workflow**

1. **Stage** → `git add <file>`
2. **Commit** → `git commit -m "message"`
3. **Push** → `git push origin main`
4. **Pull** → `git pull origin main`
