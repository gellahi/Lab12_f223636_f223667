# Git Commands Task

This repository demonstrates the usage of various Git commands, including `git revert`, `git reset`, `git stash`, and `git rebase`, through practical scenarios. The project is based on a Java application where two partners collaborate on features and manage commits effectively.

## Table of Contents

1. [Task Overview](#task-overview)
2. [Git Revert](#git-revert)
3. [Git Reset](#git-reset)
4. [Git Stash](#git-stash)
5. [Git Rebase](#git-rebase)

## Task Overview

This task is divided into four main parts, each demonstrating a different Git command in a collaborative workflow with Java code.

### Prerequisites

- Git installed on your machine.
- Basic understanding of Git commands and Java programming.

## Git Revert

`git revert` is used to create a new commit that undoes the changes of a specific previous commit. This is a safer option for collaborative workflows as it does not erase the commit from history.

### Steps

1. **Setup Repository**  
   Partner A: Create a new repository and clone it.
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
Create Initial Commit with Java File
Partner A: Create Main.java with a simple main method.

java
Copy code
public class Main {
    public static void main(String[] args) {
        System.out.println("Welcome to the application!");
        greetUser();
    }

    public static void greetUser() {
        System.out.println("Hello, User!");
    }
}
bash
Copy code
git add Main.java
git commit -m "Initial commit with Main.java"
git push origin main
Introduce a Bug
Partner B: Modify Main.java to introduce a bug.

java
Copy code
public class Main {
    public static void main(String[] args) {
        System.out.println("Welcome to the application!");
        // greetUser(); // Removed this line to introduce a bug
    }

    public static void greetUser() {
        System.out.println("Hello, User!");
    }
}
bash
Copy code
git add Main.java
git commit -m "Introduce a bug by commenting out greetUser()"
git push origin main
Revert the Buggy Commit
Partner B: Pull the latest changes and use git revert.

bash
Copy code
git pull origin main
git revert HEAD
git push origin main
Git Reset
git reset is used to move the current branch's HEAD to a specific commit, effectively removing all commits after that point. It can operate in three modes: soft, mixed (default), and hard.

Steps
Create a Feature Branch
Partner A: Create feature-login.

bash
Copy code
git checkout -b feature-login
Initial Commit for Login Class
Partner A: Create Login.java with basic login functionality.

java
Copy code
public class Login {
    public boolean authenticate(String username, String password) {
        return username.equals("admin") && password.equals("password123");
    }
}
bash
Copy code
git add Login.java
git commit -m "Initial commit for Login class"
git push origin feature-login
Add Experimental Commit 1
Partner A: Modify Login.java to include logging.

java
Copy code
public boolean authenticate(String username, String password) {
    System.out.println("Authenticating user...");
    return username.equals("admin") && password.equals("password123");
}
bash
Copy code
git add Login.java
git commit -m "Add logging to authentication"
git push origin feature-login
Add Experimental Commit 2
Partner A: Further modify Login.java to add validation.

java
Copy code
public boolean authenticate(String username, String password) {
    if (username == null || password == null) {
        System.out.println("Invalid input");
        return false;
    }
    System.out.println("Authenticating user...");
    return username.equals("admin") && password.equals("password123");
}
bash
Copy code
git add Login.java
git commit -m "Add input validation to authentication"
git push origin feature-login
Reset to Initial Commit
Partner B: Use git reset to return to the first commit.

bash
Copy code
git log --oneline
git reset --hard <commit-hash-of-initial-login-authentication>
git push --force origin feature-login
Git Stash
git stash temporarily saves changes in your working directory without committing them, allowing you to switch branches or fix bugs and return to your stashed changes later.

Steps
Create a New Branch
Partner A: Start feature-user-profile.

bash
Copy code
git checkout -b feature-user-profile
Work on UserProfile Class
Partner A: Create UserProfile.java and start implementing a feature.

java
Copy code
public class UserProfile {
    private String name;
    private String email;

    public UserProfile(String name, String email) {
        this.name = name;
        this.email = email;
    }

    public void displayProfile() {
        System.out.println("Name: " + name);
        System.out.println("Email: " + email);
    }
}
Stash Your Work
Partner A: Save uncommitted changes.

bash
Copy code
git stash save "WIP: UserProfile feature"
Switch to Bug Fix Branch
Partner A: Create and switch to bugfix.

bash
Copy code
git checkout -b bugfix
Fix the Bug and Commit
Partner A: Fix a bug in another file and commit the changes.

java
Copy code
// Example fix in Main.java
public class Main {
    public static void main(String[] args) {
        System.out.println("Fixing critical bug!");
    }
}
bash
Copy code
git add Main.java
git commit -m "Fix critical bug in Main class"
git push origin bugfix
Return to UserProfile Feature and Apply Stash
Partner A: Switch back and apply stashed changes.

bash
Copy code
git checkout feature-user-profile
git stash pop
Git Rebase
git rebase is used to move or "replay" commits from one branch onto another, allowing you to create a linear history.

Steps
Create Separate Branches and Make Initial Changes
Partner A: Create feature-A.

bash
Copy code
git checkout -b feature-A
java
Copy code
public class Main {
    public static void main(String[] args) {
        System.out.println("Feature A work in progress.");
    }
}
bash
Copy code
git add Main.java
git commit -m "Initial commit for feature A"
git push origin feature-A
Create Changes on Main Branch
Partner B: Switch to main and make a change.

bash
Copy code
git checkout main
java
Copy code
public class Main {
    public static void main(String[] args) {
        System.out.println("Main branch update.");
    }
}
bash
Copy code
git add Main.java
git commit -m "Update Main class on main branch"
git push origin main
Rebase Feature-A with Main Branch Changes
Partner A: Fetch and rebase feature-A.

bash
Copy code
git fetch origin
git rebase origin/main
Resolve Conflicts (If Any)
Resolve any conflicts and continue rebase.

java
Copy code
public class Main {
    public static void main(String[] args) {
        System.out.println("Feature A work in progress.");
        System.out.println("Main branch update.");
    }
}
bash
Copy code
git add Main.java
git rebase --continue
Push the Rebasing Changes
Partner A: Push the feature-A branch after rebasing.

bash
Copy code
git push origin feature-A --force
Conclusion
This repository serves as a practical guide for using common Git commands effectively in collaborative workflows. Feel free to explore the code and practice the commands outlined in this README.

markdown
Copy code

### Saving the README

1. Open your code editor or text editor.
2. Create a new file named `README.md`.
3. Copy the above content into the `README.md` file.
4. Save the file.

### Adding the README to Your Repository

To add the `README.md` file to your Git repository, run the following commands in your terminal:

```bash
git add README.md
git commit -m "Add README.md with Git commands documentation"
git push origin main
This will commit the README file to your repository. Let me know if you need further adjustments or additional information!



