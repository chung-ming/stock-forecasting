# Setup Guide for Windows OS

# Table of Contents
1. [Setup Local LLM with Ollama](#section-1)
2. [Setup Python with Miniconda](#section-2)
3. [Setup Development Environment with Visual Studio Code](#section-3)

## 1. Setup Local LLM with Ollama
At the end of this section, you should be able to install Ollama on your Windows local machine and run a large-language model (LLM) version and variant of your choice.

Navigate to Ollama's download page [here](https://ollama.com/download/windows) to download Ollama to your Windows machine. Screenshot below.

![Download Ollama](/photos/screenshot-1-01.png)

Once installed, Windows Powershell auto opens showing you a command to run your first model. Screenshot below.

![Powershell showing Welcome Ollama](/photos/screenshot-1-02.png)

You will also see the Ollama program's icon on your taskbar. Screenshot below.

![Ollama program's icon](/photos/screenshot-1-03.png)

You first need to decide which LLM, which version, and which variant of the version.

Head over to Ollama's library of models page [here](https://ollama.com/library) to view the list of available LLMs. Screenshot below.

![View Ollama models](/photos/screenshot-1-04.png)

At this moment, the latest LLM released by Meta is the Llama 3.2 version. We will be using this.

Select `llama3.2` to see more details. Screenshot below.

![Llama3.2](/photos/screenshot-1-05.png)

Here, you can see the default 3B parameters version requires `2.0GB` of RAM to run. 

<details>
<summary>Did You Know: 3B vs. 1B Parameters</summary>
A 3B parameter model is generally better than a 1B parameter model for a Large Language Model (LLM) because it has more capacity to learn and represent complex patterns in language, leading to improved accuracy and performance on a wide range of NLP tasks. The additional parameters allow the model to capture more nuances and subtleties of language, resulting in better contextual understanding and more coherent text generation.
</details>

When running the model, Ollama is smart enough to check if the GPU has sufficient VRAM to run the model. Only when there is insufficient VRAM, then it will load to the DRAM and utilize the CPU for computation. 

Performing computation on the CPU is much slower compared to the GPU.

To see the different variants, click on the dropdown button, then click `View all`. Screenshot below.

![Llama3.2 variants](/photos/screenshot-1-06.png)

<details>
<summary>Did You Know: Instruct vs. Non-instruct Variant</summary>
Instruct LLM variants are fine-tuned on a specific set of instructions or tasks, allowing them to learn to follow directions and generate text that is more aligned with human intentions and values. In contrast, non-instruct variants of the same model are not fine-tuned on instructions and may generate text that is more unpredictable and potentially less aligned with human values.
</details>

<details>
<summary>Did You Know: Quantization Variants</summary>
Quantization variants, such as FP16, INT8, and BF16, are used to reduce the precision of the model's weights and activations, which can lead to significant improvements in inference speed and memory usage. By reducing the precision, the model can be run on less powerful hardware, making it more accessible and efficient for deployment in various applications.
</details>

Select the variant `3b-instruct-fp16`. Screenshot below.

![Llama3.2:3b-instruct-fp16 variant](/photos/screenshot-1-07.png)

This is a `3.21B` parameter, `F16` quantization, `6.4GB` model. 

Once you are okay with this selection, copy `ollama run llama3.2:3b-instruct-fp16` and insert into the Powershell command line. Screenshot below.

![Command ollama run llama3.2:3b-instruct-fp16](/photos/screenshot-1-08.png)

Once downloaded, the model will immediately run, and you can input a prompt like `What is love in 3 sentences` or `/bye` to exit. Screenshot below.

![LLM prompt in Powershell](/photos/screenshot-1-10.png)

For more Ollama-specific commands, select `GitHub` at the page's navbar, or click [here](https://github.com/ollama/ollama?tab=readme-ov-file#ollama) to go to Ollama's GitHub page. Screenshot below.

![Ollama's GitHub page](/photos/screenshot-1-09.png)

Other important instructions are:
* `ollama run llama3.2`: Loads and runs the model
* `ollama list`: List of models downloaded to local machine
* `ollama ps`: List of models loaded and running
* `ollama stop llama3.2`: Stop a running model
* `ollama remove lllama3.2`: Removes a model


## 2. Setup Python with Miniconda
At the end of this section, you should be able to install the Miniconda package manager on your Windows local machine, create multiple environments and run a Python version of your choice in the environment.

Navigate to Miniconda's download page [here](https://docs.anaconda.com/miniconda/miniconda-install). Screenshot below.

![Miniconda's download page](/photos/screenshot-2-01.png)

When installing, accept all default selections.

Once installed, search for `Anaconda Prompt` in the Windows Taskbar. Screenshot below.

![Search for Anaconda Prompt](/photos/screenshot-2-02.png)

Check if conda is running by typing `conda --version`. Screenshot below.

Check the installed default Python version by typing `python --version`. Screenshot below.

![Check Miniconda installation successful](/photos/screenshot-2-03.png)

Open Command Prompt and type in `conda`. You will see an error like this:

```
'conda' is not recognized as an internal or external command,
operable program or batch file.
```

To fix this, the system needs to be able to find the Conda executable.

At Windows Taskbar, search for `Environment Variables`. Screenshot below.

![Search for Environment Variables](/photos/screenshot-2-04.png)

In the `System Properties` window, click on the `Environment Variables` button. Screenshot below.

![CLick Environment Variables button](/photos/screenshot-2-05.png)

In the `Environment Variables` window, we need to update the `Path`. However, we are unsure whether to update `Path` in `User Variable` or `System Variable`. Screenshot below.

![Environment Variables window](/photos/screenshot-2-06.png)

To know where miniconda is installed, open `Anaconda Prompt` again and type in `where python`. Screenshot below.

For the path with `miniconda3`, if the path starts with a `C:\Users\...`, it means Miniconda was installed at user-level and not system-level. 

In my example, Miniconda was installed at user-level. 

![Anaconda Prompt](/photos/screenshot-2-07.png)

Navigating back to the `Environment Variables` window, in the `User variables` window at the top-half of the window, double-click on `Path`. Screenshot below.

![Environment Variables window](/photos/screenshot-2-06.png)

In the `Edit environment variable` window, add the new paths to `miniconda3` and `miniconda3/Scripts`. Then click `OK`. Screenshot below.

![Edit environment variable window](/photos/screenshot-2-08.png)

Open a new Command Prompt terminal and type `conda init` to initialize conda. Screenshot below.

![Initialize conda in command prompt](/photos/screenshot-2-09.png)

Then, type `conda activate`. The `(base)` indicator will appear. Screenshot below.

![Activate conda in command prompt](/photos/screenshot-2-10.png)

<details>
<summary>Did You Know: Conda's Base</summary>
Base is the default virtual environment that is created when you install Conda, and it contains the core packages and dependencies required by Conda. The (base) label is displayed in the command prompt or terminal to indicate that you are currently operating within the base environment, rather than a specific project or application environment.
</details>

(Optional) Follow along to learn other commands:
`conda env list`: Lists all existing Conda virtual environments on the system.

`conda activate`: Activates the default Conda environment (usually the base environment).

`conda create --name py311`: Creates a new Conda environment named "py311".

`conda activate py311`: Activates (Enters) the "py311" environment.

`conda install python=3.11`: Installs Python 3.11 in the currently active environment (in this case, "py311").
> If you are in the (py311) environment, then Python is installed in that environment only. THe (base) environment still has Python 3.12 installed. 

`python --version`: Checks the Python version installed for a particular environment.

`conda deactivate py311`: Deactivates (Exits) the "py311" environment and returns to the base environment.

`conda env list`: List all existing Conda virtual environments on the system.
> This time, you have two environments listed.

`conda env remove --name py311`: Deletes the "py311" environment and all its dependencies.


## 3. Setup Development Environment with Visual Studio Code
At the end of this section, you should be able to install the Visual Studio Code editor on your Windows local machine, install extensions to enhance the development environment, create a Python virtual environment, and execute Python code in a Jupyter notebook.

Navigate to the Visual Studio Code download page [here](https://code.visualstudio.com/download). Screenshot below.

![Visual Studio Code download page](/photos/screenshot-3-01.png)

Once downloaded and installed, the next step is to transform the editor to a Python integrated development environment.

Go ahead to install these recommended extensions:
* Jupyter by Microsoft (Extension Pack)
* Python Extension Pack by Don Jayamanne (Extension Pack)
* Path Intellisense by Christian Kohler
* Rainbow CSV by mechatroner
* GitHub Markdown Preview by Matt Bierner (Extension Pack)

It's best practice to create a workspace. One of the beneift is you can double-click it to load the entire workspace into Visual Studio Code. 

Create workspace by clicking the following: File > Save Workspace As. Screenshot Below.

![Visual Studio Code save as workspace](/photos/screenshot-3-02.png)

In the example, the Workspace is saved as `setup.code-workspace` in a folder named `setup`. Screenshot below.

![Visual Studio Code name the workspace](/photos/screenshot-3-03.png)

Open the Command Prompt by selecting the following: Terminal > New Terminal. Screenshot below.

![New terminal](/photos/screenshot-3-14.png)

Switch the terminal from `Powershell` to `Command Prompt`. Screenshot below.

![Switch terminal](/photos/screenshot-3-15.png)

Upgrade pip with `python -m pip install --upgrade pip`, followed by installing the jupyter package `python -m pip install jupyter`. Screenshot below.

![Upgrade pip and install jupyter](/photos/screenshot-3-16.png)

Now, the Python virtual environment needs to be created, and a Python interpreter needs to be selected.

At the top-right corner of Visual Studio Code, click on the defaulted Python Interpreter. 

It should be in the format `base(<Python version>)`. Take note of the path. Screenshot below.

![Visual Studio Code base interpreter path](/photos/screenshot-3-04.png)

Hit `Ctrl + Shift + P` to open up Visual Studio Code's Command Pallette. Screenshot below.

Type `Python Interpreter` and select `Python: Select Python Interpreter`.

![Select Python interpreter dropdown](/photos/screenshot-3-05.png)

Select `Create Virtual Environment`. Screenshot below.

![Select create virtual environment](/photos/screenshot-3-06.png)

Select `Venv` to create a virtual environment. Screenshot Below.

![Select venv](/photos/screenshot-3-07.png)

Select `Enter interpreter path`. Screenshot below.

![Select enter interpreter path](/photos/screenshot-3-08.png)

Select `Find`. Screenshot below.

![Select find](/photos/screenshot-3-09.png)

Select the interpreter path that corresponds to the base interpreter at the top-right of Visual Studio Code. 

The file path should end with a `python.exe` application. Screenshot below.

Click `Select Interpreter`.

![Navigate to the interpreter path](/photos/screenshot-3-10.png)

Once done, Visual Studio Code creates a hidden `.venv` file in your workspace. Screenshot below.

![.venv file created](/photos/screenshot-3-11.png)

To test if the Python development environment is working, write a simple program like the example below: 

```
!pip3 install numpy
import numpy as np
numbers = np.array([1, 2, 3, 4])
numbers
print("Sum: ", np.sum(numbers))
```

Click `Run All`. Screenshot below.

![Python program](/photos/screenshot-3-12.png)

If it runs successfully, the results will be displayed for each cell (where applicable). Screenshots below.

![Python program runs successfully](/photos/screenshot-3-18.png)

To view the stored variabels, select the `Variables` tab. Screenshot below.

![View variables](/photos/screenshot-3-19.png)

To test if Visual Studio Code have access to the LLM running locally, create the Python program as below:

```
%%capture
!pip3 install -r langchain-ollama

from langchain_ollama import ChatOllama

try:
    llm = ChatOllama(model="llama3.2:3b-instruct-fp16")
    print("ChatOllama instance created successfully!")
except Exception as e:
    print("Error creating Ollama instance. Check if ollama is running with the command `ollama ps`", e)

response = llm.invoke("What is love in 3 sentences")
response.content
```
Screenshot below.

![Test Ollama program](/photos/screenshot-3-20.png)
