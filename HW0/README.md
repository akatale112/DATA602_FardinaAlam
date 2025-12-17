# HW0: Computing Environment

## Objective

Throughout the semester, you will work with various software packages, including Python, Pandas, Jupyter Notebook, Google Colab, PyTorch, and others. Installing these packages and managing software dependencies can sometimes be challenging. This assignment focuses on ensuring you have the necessary tools installed and working properly. Installing those packages and getting started can often be a hassle because of software dependencies.

You have the following options for setting up your environment:

* Install the different software packages on your own machine (most of these packages should have tutorials to install them on different OSs). If you have a Linux box or a Mac, this should be possible; it may be more difficult with Windows. In any case, although we will try our best, we will likely not be able to help you with any problems.

* Use Docker (as discussed below). If you have a reasonably modern machine (within last 3-4 years), this should generally work fine, but with older laptops, the performance may not be as good. See below for more details on this.

* (If you're ambitious) You can use functionality from VSCode (one of Microsoft's IDEs) to edit, run, and display Jupyter Notebooks all within one application.


Now, for this assignment, you have to do the following tasks:
---
### Git & Github

Git is one of the most widely used version control management systems today, and invaluable when working in a team. GitHub is a web-based hosting service built around git -- it supports hosting git repositories, user management, etc. There are other similar services, e.g., bitbucket.

For this course, you will use GitHub to manage and collaborate on your class projects and any other relevant work. While the use of GitHub for the class will be minimal, it is highly recommended for managing your own projects and collaborating effectively.

#### 1.  Setting Up Your GitHub Repository

Repositories hosted on github for free accounts are public; however, you can easily sign up for an educational account which allows you to host 5 private repositories. More details at: https://education.github.com/

##### Setting up a GitHub Account 

- Create an account on Github: https://github.com
- Generate and associate an SSH key with your account
    - Instructions to generate SSH Keys: https://help.github.com/articles/generating-ssh-keys#platform-linux
        - Make sure to remember the passphrase
    - Go to Profile: https://github.com/settings/profile, and SSH Keys (or directly: https://github.com/settings/ssh)
    - Add SSH key to your GitHub account (https://github.com/settings/ssh)
 
##### Repository Setup:

Prepare Files, Fork and Clone Repository:

* Create a .txt file on your computer in an empty directory answering the question "Why are you interested in taking DATA602?". Then, in the same empty directory, create an empty file called data.DAT. It is crucial the file is called only data.DAT.
* Then, fork this directory by clicking fork in github. In your forked copy of the repository, go to 'Code', and copy the https clone key.
* Open a command prompt on your computer, and go to some empty directory. Then, type 'git clone key' into the command line (where key is whatever https link github gave you).
* Move the two files you created into the cloned directory (your downloaded fork).

Upload Files to GitHub:

Now you need to find a way using a standard git reference to upload your answers in the text file to your fork on github on the main branch, which should be public. However, using a .gitignore, your data.DAT file should not be on the main branch of your repository. You need to use a .gitignore for this task to receive full credit.

The documentation on git is available here (https://git-scm.com/docs). Please note you should be mostly interested in the add command, and instructions for making a .gitignore here (https://docs.github.com/en/get-started/getting-started-with-git/ignoring-files).

*** Basic Git Commands to Know: *** 
- Familiarize yourself with the basic git commands
    - At a minimum, you would need to know: `clone`, `add`, `commit`, `push`, `pull`, `status`
    - But you should also be familiar with how to use **branches**

- You can't push to the main class repository, but feel free to do *pull requests* on the main class repository if you spot any errors or if you think something could be improved.

##### Create a GitHub Page:

Create a GitHub Pages site for your repository. Follow the instructions here (https://git-scm.com/docs) to set up a .github.io page for your repository.

---
### 2. Installing Python and Jupyter/IPython

We will be using Python for most of the assignments. Python is easy to pick up, and we will also provide skeleton code for most of the assignments. 

IPython is an enhanced command shell for Python, that offers enhanced introspection, rich media, additional shell syntax, tab completion, and rich history. 

**Jupyter/IPython Notebook** started as a web browser-based interface to IPython, and proved especially popular with Data Scientists. A few years ago, the Notebook functionality was forked off as a separate project, called [Jupyter](http://jupyter.org/). Jupyter provides support for many other languages in addition to Python. Several other projects have been started in the recent years, inspired by the idea of Notebooks, e.g., Zeppelin.

Use the command listed above to start a docker container with Jupyter. On your local browser, go to: http://localhost:8888 (which requires you to enter the token). 

* You should see the Notebooks in the `notebooks/` directory. Click to open the "Jupyter Getting Started" Notebook, and follow the instruction therein.

* You should play with the Notebook to try out different Python commands. You can try creating a new notebook.

### 3. Setting up Google Colab

Google Colab (https://colab.research.google.com/) is a cloud-based environment that will be useful for running more extensive computations without stressing your local machine. Ensure that you can access Google Colab through your Google account. Create a simple notebook, run a Python cell, and confirm it works. For more details, check the tutorial: https://colab.research.google.com/drive/16pBJQePbqkz3QFV54L4NIkOn1kwpuRrj

### 3. Install PyTorch

Install PyTorch (https://pytorch.org/) on your machine. Follow the instructions on the PyTorch website (https://pytorch.org/get-started/locally/) for your specific operating system. Run a quick test to ensure PyTorch is installed correctly.

PyTorch is a deep learning framework that provides a flexible and easy-to-use environment for building machine learning models. It's particularly popular in research and industry for tasks involving neural networks. We will use PyTorch for our last HW of Deep Learning. 

You will need to install PyTorch on your local machine by following the instructions on the PyTorch official website. Make sure to choose the installation command that matches your system configuration (OS, package manager, CUDA version). After installation, create a simple script that verifies the installation by printing the installed PyTorch version and confirming if a GPU is available for use:


import torch
print("PyTorch Version: ", torch.__version__)
print("GPU Available: ", torch.cuda.is_available())

Run this script in both your local environment and Google Colab, then include the outputs as screenshots in your HW0 Assignment.ipynb

NOTE THAT: Creating a virtual environment for PyTorch (or any other Python package) is highly recommended, though not strictly necessary. A virtual environment helps isolate your project's dependencies, ensuring that different projects do not interfere with each other. This is especially useful when working with different versions of libraries like PyTorch, TensorFlow, or others. HOWEVER, THIS IS TOTALLY YOUR CHOICE! Here are some links to check out how to create pythom virtual environment:

* https://docs.python.org/3/tutorial/venv.html
* https://gist.github.com/Ravi2712/47f070a6578153d3caee92bb67134963
---
### BONUS OPTIONAL TASK: (5 points)

#### Docker 


Using Docker is not required (I don't use it). Docker is a software technology providing `containers`, that provides an additional layer of abstraction and automation of operating-system-level `virtualization` on Windows and Linux. Here is a nice introductory blog post that describes virtualization and containers: https://medium.freecodecamp.org/a-beginner-friendly-introduction-to-containers-vms-and-docker-79a9e3e119b. Briefly speaking, a virtual machine (VM) is an emulation of an (`guest`) operating system on a computer (with potentially a different `host` operating system). Linux is the most common guest OS that is used, especially since Apple and Microsoft make it difficult to emulate their OSes. `Containers` look like a VM, but share the host kernel (if possible) to be more efficient, both in terms of the memory used and the slowdown.

Docker is perhaps the most popular container technology at this time, and is widely used to package and ship applications. There are many pre-existing `images` that can be pulled from https://hub.docker.com/ (or elsewhere) to quickly install and run different software (as you will see below).

- To get started, install Docker by following the instructions on the webpage for your machine: https://docs.docker.com/engine/installation/. We suggest the Stable Channel of the Community Edition.
- Follow the appropriate `Getting Started` guide to make sure that Docker is working as expected.
	- Macs: https://docs.docker.com/docker-for-mac/
	- Windows: https://docs.docker.com/docker-for-windows/
- We will use the `Jupyter Notebook Data Science Stack` for now. You can start it using the following command in the commandline -- make sure you're in the git directory. More detailed description of the image (thanks, José Calderón, for updating this in Summer 2021!) is available at: https://hub.docker.com/r/jmct/cmsc320
	- docker run -it -v $(pwd)/project0:/home/jovyan/notebooks  --rm -p 8888:8888 jmct/cmsc320

	Note: If this command doesn't work, please replace `$(pwd)` with the current git directory.
- Quick explanation of the above command (don't worry if you don't follow this right now):
	- `-p 8888:8888` maps the 8888 port on the host OS to the 8888 port on the guest container. So if you were to go to http://localhost:8888, it will redirect to the 8888 port on the container - Jupyter Notebook starts a web server on that port on the guest.
	- `-v $(pwd)/project0:/home/jovyan/notebooks` mounts the current project0 directory on the guest, so that everything in project0 directry will be available in `notebooks` directory on the guest. $(pwd) automatically runs the `pwd` unix command and places the result directly, so that you don't have to type the location of the git directry manually.
	- `jupyter/datascience-notebook` tells docker which image to pull from the Docker Hub. The first time you do this, it will take a few minutes to download everything it needs.
- Once everything is initialized and the notebook starts, you can connect it to by opening your web browser and going to: http://localhost:8888/tree?token=279fb5e0fc0f240a90f913e7b9c9c068f36543a7d9544663  --- the `token` will be different for you. Look for it in the output of the command above.


##### VSCode (OPTIONAL)

Using VSCode is not required (I don't use it), but if you'd like to use Jupyter Notebooks from within the VSCode IDE, you can use this template repository made by a Microsoft employee: [ml-devcontainer](https://github.com/jlorich/ml-devcontainer). This requires Docker and VSCode to be installed, but will allow you skip using a web-browser for interacting with your Notebooks.

You should only try this option if you are comfortable with the steps described in the `readme.md` in the above repo. It's completely fine if those instructions do not seem clear to you, but you probably shouldn't use this option for this course.

---
### Assignment Deliverables: 

* ##### 1. Complete the function in the `HW0 Assignment` Notebook as instructed in the notebook (10 points). 

Additionally, you need to include the following in the HW0 Assignment Notebook:

* ##### 2. Provide GitHub Repository URL (10 points):
 Include the URL of your public GitHub repository in the HW0 Assignment.ipynb file. This repository should include:
  - why_interested.txt file
  - A correctly configured .gitignore file to exclude data.DAT

* ##### 3. Provide GitHub Page URL (04 points):
  - Include the URL of your GitHub Page site in your HW0 Assignment.ipynb file.

* ##### 4. Add Screenshots (06 points):
  Include screenshots in the HW0 Assignment.ipynb file that demonstrate the successful setup of:
  - Python: Run some Python code and show the output.
  - Google Colab: : Run any code and show the output.
  - PyTorch: Include the script output showing the PyTorch version and GPU availability.

If you are completing the optional bonus task, you should also provide relevant screenshots at the end of the HW0 Assignment Notebook.

REMEMBER: Each screenshot must clearly show your name and ID. You can add this information manually. 

#### Finally, Upload the Notebook: Rename the notebook "HW0 Assignment.ipynb" to "HW0 Assignment_DATA602_YourLastName.ipynb" and upload the completed .ipynb file to Gradescope.


WARNING: You should ensure that your `ipynb` file is your _completed_ assignment. A common error case is that students submit the original `ipynb` and not their updated one! This can happen if you're not loading the docker container correctly and so the work does not save to your host machine.
