# TDT4173 PROJECT GUIDE

# Table of Contents
1. [Setup](#setup)
2. [When working on the project](#when-working-on-the-project)

# Setup

**NOTE** this guide assumes that everyone has a mac.

This guide is about how to make a virtual environment. Having a virtual environment is cruical for such a project. A virutal environment can be described as follows,

*"A virtual environment is like a separate bubble for your Python projects, keeping their libraries and tools from mixing and causing problems with each other or your computer's main setup."*

To setup a virtual environment perform the following command.

```bash
python3.10 -m venv sigmoidwarriors
```

To activate the virtual environment run the following command. 

```bash
source sigmoidwarriors/bin/activate
```
You'll see the virtual environment's name in your command prompt, indicating that it's activated.

The project has a requirments.txt. All our dependecies will reside there. To install all the necessary dependenices perform the following command.

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

Now we must create a fitting kernal to run the jupyter notebook.

```bash
ipython kernel install --user --name=sigmoidwarriors
```

Now restart vscode. Go inside your desired notebook and select the right jupyter kernel.

----------------------------------------------------------------------

# When working on the project

When you open vscode, first go into the folder in which you created your virtual environment. If you followed the setup this will be inside the data folder. If you want to navigate to the folder from the terminal type the following.

```bash
cd data
```
Since you have already created a virtual environment, you only need to activate it.

```bash
source sigmoidwarriors/bin/activate
```

When you install new packages with "*pip install package-name*" you should add this to the requirments.txt file. That is done with the following command.

```bash
pip freeze > requirements.txt
```

If new packages have been added to the requirments.txt file you can easily add them inside your virtual environment like so.

```bash
pip install -r requirements.txt
```

Moreover it is best practise **NOT** to *push* your virtual environment folder (sigmoidwarriors). One should make use of the requirment.txt file.

To deactive the virtual environment perform the following command.

```bash
deactivate
```

**Letsgo teeeam!!**
