# Ollama mit Open-Webui

# Depencies:

- Python 3.11 / pipx
- pip
- scoop

  

# Install Ollama:

Visit [Ollama](https://ollama.com/) and download the file, fitting your OS (If its down, load the file from this repo).

Follow the instructions of the installer (it will automatically being installed at the home disk of your system, ensure that you have enough space left)

After installation, you can test the functionality by opening a shell (e.g. powershell on Windows) and type in ollama, it should output something like this:

````
Usage:
  ollama [flags]
  ollama [command]

Available Commands:
  serve       Start ollama
  create      Create a model from a Modelfile
  show        Show information for a model
  run         Run a model
  stop        Stop a running model
  pull        Pull a model from a registry
  push        Push a model to a registry
  list        List models
  ps          List running models
  cp          Copy a model
  rm          Remove a model
  help        Help about any command

Flags:
  -h, --help      help for ollama
  -v, --version   Show version information

Use "ollama [command] --help" for more information about a command.
````



## Post Install:

Run
````
ollama pull mistral:7b
````

This will pull the LLM Mistral in the variant 7b, a complete list of all LLMs can bei found here [Ollama Models](https://ollama.com/search)

the syntax to pull the models is:

`[modelname]:[Variant]`



==**ATTENTION!**==

Ollama will allways pull the LLMs onto your Home Disk, to avoid this, you can enter environement variables:



### Windows

Open Setting go to System > Information > Parent Links > Advanced System settings > Advanced > Environement Variables

Click on New and type in:

Name of the Variable
````
OLLAMA_MODELS
````

Value of the Variable

`
the\path\you\want
`

e.g.
````
D:\ollama\models
````



# Install open-webui

Get the files here: [open-webui/open-webui](https://github.com/open-webui/open-webui)

There are three options:

1. Run a Docker - No hassel, no compiling
2. Compile the files your own
3. Using pip



## Install using pip

With a bit of luck you just need to enter:

````
pip install open-webui
````

With a bit of unluck, you then get an error messages like this:

`
ERROR: Could not find a version that satisfies the requirement open-webui (from versions: none)
ERROR: No matching distribution found for open-webui
`

This error comes with a wrong python Version (open-webui only supports 3.11)


In this case you have 2 options:
- Create a virtual environment with a python 3.11 version installed (recommended)
- Install the python version onto your system (not recommended)



## Virtual Environements with pipx


### For Windows

Install Scoop, by opening powershell and typing in:

```
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser
Invoke-RestMethod -Uri https://get.scoop.sh | Invoke-Expression
```

Open a new Powershell window and type in:

````
scoop install pipx
`````
and 
````
pipx ensurepath
````

Open another new ps window and type in:
````
pipx install --fetch-missing-python --python 3.11 open-webui
````
If you`re getting an error like:

`
No executable for the provided Python version '3.11' found in py launcher. Please make sure the provided version is listed when running "py --list".
`
  
Try updating pipx with pip, by using this command:

````
pip install --upgrade pipx
````  
  
This should work and successfully install open-webui in an isolated virtual environment.
  
  

## Starting open-webui

In your Powershell window, run:
````
open-webui serve
 ````
This is starting the service, the website should be reachable at [your localhost:8080](http://localhost:8080/)

Common Error:
````
[Errno 13] error while attempting to bind on address ('0.0.0.0', 8080): der zugriff auf einen socket war aufgrund der zugriffsrechte des sockets unzulässig
````
This shows, that the port is already in use and can't be blocked by open-webui. You need to kill the programm, thats blocking Port 8080.


# Finishing the Installations

If everything is working, you just need to create an Account (it's local only) and then see a ChatGPT like GUI. 

By clicking at the "Arena Model" at the top of the left, you can choose your preferred LLM, which answers your questions.

Enjoy!
