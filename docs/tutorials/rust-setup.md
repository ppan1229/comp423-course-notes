# Setting up a dev container for Rust

### Attributions:

* Primary author: [Paige Pan](https://github.com/ppan1229)
* Reviewer: [Baotran Nguyen](https://github.com/bnln7)

### Part 0: Introduction

In this tutorial, you will learn how to set up a dev container for Rust and write a "Hello World" program.
You might be wondering **why dev containers are important!**
Dev containers play an important role in creating consistent development environments across different machines.
When working with others, dev containers save you time that you would have spent manually setting up your environment.
The language, tools, and dependencies are all ready to use in a dev container.

### Prerequisites

For this tutorial, you will need the following:

+ [Git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) - A version control system.
    + If you are new to Git, you can reference the [Git Documentation](https://git-scm.com/docs).
+ A [GitHub](https://github.com) account.
+ [Visual Studio Code](https://code.visualstudio.com/Download) - A source code editor.
+ [Docker Desktop](https://www.docker.com/products/docker-desktop/) - Allows you to build, run, and deploy containers.
+ Knowledge of command line basics. 

### Part 1: Creating Your Local Repository

1. Create a new directory where all of your files for this project will be stored. Make sure to change (`cd`) into it!
``` title="terminal"
mkdir rust-tutorial
cd rust-tutorial
```

2. We'll create our repository next. This command initializes your folder as a new git repository.
``` title="terminal"
git init
```

3. Next, create a `README` file in your directory.
The following commands will add the contents to, stage, and commit your file.
``` title="terminal"
echo "# [Rust Tutorial](https://ppan1229.github.io/comp423-course-notes/tutorials/rust-setup/)" > README.md
git add README.md
git commit -m "First commit with README file."
```

### Part 2: Connecting to GitHub

#### Creating a GitHub Repository

1. Log into GitHub and [create a new repository](https://github.com/new).
2. Set the repository name to **"Rust Tutorial"**. Set the description to **"Setting up a dev container for Rust."** Leave all other settings alone, then click "Create repository."

#### Linking Local Repository to GitHub

3. Use the following command, replacing `<your-username>` with your GitHub username.
``` title="terminal"
git remote add origin https://github.com/<your-username>/rust-tutorial.git
```
4. Make sure your current branch's name is "main" using `git branch`. If you need to change the name of your branch, use
``` title="terminal"
git branch -M main
```
5. Push your main branch to your GitHub remote repository origin.
``` title="terminal"
git push --set-upstream origin main 
```
6. Now, if you refresh your GitHub repository page, you should see the commit you just pushed to remote. As you continue to commit and push changes, you can use `git log` to view your project history.

### Part 3: Creating and Opening a Dev Container

#### Creating the Dev Container

1. Open your `rust-tutorial` directory in VS Code.
2. Navigate to extensions and install **Dev Containers**. 
3. At the root of your directory, create a new `.devcontainer` directory using `mkdir` again. In this new directory, add a new file named `devcontainer.json`. This file defines the configuration for your development environment. Though it can be customized, we'll give you everything you need for now. Add the following content to your file:
``` title="devcontainer.json"
{
  "name": "Rust Tutorial",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  },
  "postCreateCommand": "rustc --version"
}
```
+ `name` is the name of your dev container.
+ `image` is the Docker image to use. A Docker image contains all of the files needed to run a container. In this case, we're using a base image of Rust from Microsoft.
+ `customizations` adds extensions and other useful configurations that other developers will need to work on your project.
+ `postCreatecommand` is the command that runs after your container is created. In this case, we check that we have the most recent version of Rust.

#### Opening the Dev Container

!!! info

    You must have Docker running before you proceed with the following steps.

1. Reopen the project in the container by pressing `Ctrl + Shift + P` on Windows, or `Cmd + Shift + P` on Mac. Type in "Dev Containers: Reopen in Container" and select the option. After the setup concludes, close your current terminal and open a new one. Running `rustc --version` will show that your dev container is running a recent version of Rust! 🎉

### Part 4: Your First Rust Project

Now, you are ready to test out Rust with a simple "Hello World" project :)

1. Change to your directory with `cd rust-tutorial`.

2. Use `cargo new hello_world --vcs none` to create a binary project. `cargo new` creates a new directory named `hello_world` in the current location. `--vcs none` ensures that no new git repository is initialized.

3. Check out your new directory! Navigate to `src/main.rs`.

4. Add the following code to `main.rs` and save your file.
``` title="main.rs"
fn main() 
{
    println!("Hello World!");
}
```

5. Use `cargo build` to compile the program. You can now run the compiled file outputted by using `./target/debug/hello_world`. `cargo build` does not run the executable file for you.
    1. `cargo build` is similar to COMP 211's `gcc`, which is used to mainly compile C and C++. Both commands compile source code files and output executables. However, `gcc` does not include built-in dependency or package management like `cargo`.

6. You can use `cargo run` if you want to skip the steps of finding and running the compiled file when you use `cargo build`. This command compiles (if needed) and runs your program all in one step. 

🎉 **Congratulations! You are done with your first dev container and Rust project!**🎉

### References

+ [The Cargo Book - Creating a New Package](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html)

+ [Starting a Static Website Project with MKDocs](https://doc.rust-lang.org/cargo/guide/creating-a-new-project.html)