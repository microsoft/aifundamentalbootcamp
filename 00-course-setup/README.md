# Getting Started with this course

To ensure your success, this page outlines setup steps, technical requirements, and where to get help if needed.

## Setup Steps

To start taking this course, you will need to complete the following steps.

### 1. Fork this Repo

[Fork this entire repo](https://github.com/microsoft/aifundamentalbootcamp/fork) to your own GitHub account to be able to change any code and complete the challenges.

### 2. Configure your working environment

#### 2.1. Create a Github Codespaces environment (RECOMMENDED OPTION)

To avoid any dependency issues when running the code, we recommend running this course in a [GitHub Codespaces](https://github.com/features/codespaces).

This can be created by selecting the **Code** option on your forked version of this repo, selecting the **Codespaces** option and selecting the **Create codespace on main** option.

![Dialog showing buttons to create a codespace](./images/who-will-pay.webp)

Github Codespaces will automatically open the Visual Studio Code online version, with the cloned repository. The environment will be ready to execute the code from this bootcamp.

If you selected this option (CodeSpaces), you can continue with the Azure OpenAI setup instructions in [Section 3](#3-using-the-azure-openai-service).

> [!CAUTION]
> **Storing Your API Keys**
>
> Keeping your API keys safe and secure is important when building any type of application. We recommend not to store any API keys directly in your code. Committing those details to a public repository could result in security issues and even unwanted costs if used by a bad actor.

One of the best ways to keep your API keys secure when using GitHub Codespaces is by using Codespace Secrets. Instructions are provided below for those that choose to run their code locally on their computer, but if this is your chosen method, it is critical that you obfuscate your secrets!  Never use and commit an .env file with hard coded values in it to your fork, as by default, the fork is public.  

#### 2.2. How to Run locally on your computer

> [!IMPORTANT]
> If you are using Github Codespaces you can skip **section 2.2** and its substeps.

To run the code locally on your computer, you need to have the following tools:

* Git
* Version 3.12 of [Python](https://www.python.org/downloads/)
  * Python packages: ipywidgets, matplotlib, numpy, pandas, tqdm, python-dotenvv, openai, tiktoken, plotly, scikit-learn, pandas

To then use the repository, you need to clone it:

```shell
git clone https://github.com/microsoft/aifundamentalbootcamp.git
cd aifundamentalbootcamp
```

Once you have everything checked out, you can get started!

#### 2.2.A. Using a local Visual Studio Code with the Python support extension

We recommend using the [Visual Studio Code (VS Code)](https://code.visualstudio.com/) editor with the [Python support extension](https://marketplace.visualstudio.com/items?itemName=ms-python.python) installed for this course. This is, however, more of a recommendation and not a definite requirement

> [!NOTE]  
> By opening the course repository in VS Code, you have the option to set the project up within a container. This is because of the [special `.devcontainer`](https://code.visualstudio.com/docs/devcontainers/containers?itemName=ms-python.python) directory found within the course repository. More on this later.
>
> Once you clone and open the directory in VS Code, it will automatically suggest you install a Python support extension.
>
> If VS Code suggests you re-open the repository in a container, decline this request in order to use the locally installed version of Python.

#### 2.2.B. Running in a container

An alternative to setting everything up on your computer or Codespace is to use a container. The special `.devcontainer` folder within the course repository makes it possible for VS Code to set up the project within a container. This will require the installation of Docker, and quite frankly, it involves a bit of work, so we recommend this only to those with experience working with containers.

### 3. Using the Azure OpenAI Service

You will need access to the Azure OpenAI service and an API key to run this code.

If this is your first time working with the Azure OpenAI service, please follow this guide on how to [create and deploy an Azure OpenAI Service resource.](https://learn.microsoft.com/azure/ai-services/openai/how-to/create-resource?pivots=web-portal)

### 4. Finalize the configuration settings for the Visual Studio Code environment

> [!IMPORTANT]  
> To properly run the code from this bootcamp follow these **[instructions](./SETUP.md)** before executing the labs.

## Disclaimer

> [!NOTE]
> This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information read the Code of Conduct FAQ or contact [Email opencode](opencode@microsoft.com) with any additional questions or comments.
