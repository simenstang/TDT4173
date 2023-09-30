# TDT4173 PROJECT GUIDE

# Setup

Note this guide assumes that everyone has a mac.

This guide is about how to make a virtual environment. Having a virtual environment is cruical for such a project. A virutal enviornment can be described as follows,

"A virtual environment is like a separate bubble for your Python projects, keeping their libraries and tools from mixing and causing problems with each other or your computer's main setup."

To setup a virtual environment perform the following command.

```bash
python3.10 -m venv venv
```

To activate the virtual environment run the following command. 

```bash
source venv/bin/activate
```
You'll see the virtual environment's name in your command prompt, indicating that it's activated.

The project has a requirments.txt. All our dependecies will reside there. To install all the necessary dependenices perform the following command.

```bash
pip install --upgrade pip
pip install -r requirements.txt
```

To deactive the virtual environment perform the following command.

```bash
deactivate
```

----------------------------------------------------------------------

# When working on the project

When you install new packages with *pip install package-name* you should add this to the requirments.txt file. That is done with the following commmand.

```bash
pip freeze > requirements.txt
```

If new packages have been added to the requirments.txt file you can easily add them inside your virtual environment like so.

```bash
pip install -r requirements.txt
```

Letsgo teeeam!!
