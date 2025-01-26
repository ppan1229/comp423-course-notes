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
+ A [GitHub](https://github.com) Account.
+ [Visual Studio Code](https://code.visualstudio.com/Download) - A source code editor.
+ [Docker Desktop](https://www.docker.com/products/docker-desktop/) - Allows you to build, run, and deploy containers.
+ Knowledge of command line basics. 

### Part 1: Creating Your Repository

First, create a new directory where all of your files for this project will be stored. Make sure to change (cd) into it!
``` bash
mkdir rust-tutorial
cd rust-tutorial
```

We'll create our repository next. This command initializes your folder as a new git repository.
``` bash
git init
```

Next, create a README file in your directory.
The following commands will add the contents to, stage, and commit your file.
``` bash
echo "# [Rust Tutorial](https://ppan1229.github.io/comp423-course-notes/tutorials/rust-setup/)" > README.md
git add README.md
git commit -m "First commit with README file."