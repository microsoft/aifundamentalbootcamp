# Setup Your Dev Environment

After setting up the [working environment](./README.md), it is time to configure specific items to make the code work.

## 1. Executing Assignments

This section provides general guidance related to executing those assignments.

### 1.1. Python Assignments

Python assignments are provided either as applications (`.py` files) or Jupyter notebooks (`.ipynb` files).

* To run the notebook, open it in Github Codespaces Visual Studio Code, then click **Select Kernel** (at top right) and select the default **Python** option shown. You can now **Run All** to execute the whole notebook.
* To run Python applications from command-line, follow assignment-specific instructions to ensure you select the right files and provide required arguments.

## 2. Configuring Providers

Assignments **may** also be setup to work against one or more Large Language Model (LLM) deployments through a supported service provider like Azure OpenAI. This provides a **hosted endpoint** (API) that we can access programmatically with the right credentials (API key or token). In this course, we discuss theis provider:

* [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/) for OpenAI models with enterprise readiness in focus.

**You will need to use your own accounts for these exercises**. Some guidance for signup:

| Signup | Cost | API Key | Playground | Comments |
|:---|:---|:---|:---|:---|
| [Azure](https://aka.ms/azure/free)| [Pricing](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/)| [SDK Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart)| [Studio Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart) |  [Must Apply Ahead For Access](https://learn.microsoft.com/azure/ai-services/openai/)|
| | | | | |

Follow the directions below to **configure** this repository for use with Azure OpenAI. Assignments that require a specific provider will contain one of these tags in their filename:

* `aoai` - requires Azure OpenAI endpoint, key and deployment name

Assignments will simply error out on missing credentials.

### 2.1. Create `.env` file

We assume that you have already read the guidance above, signed up with the relevant provider, and obtained the required authentication credentials (API_KEY). In the case of Azure OpenAI, we assume you also have a valid deployment of an Azure OpenAI Service (endpoint) with at least one GPT model deployed for chat completion.

The next step is to configure your **local environment variables** as follows:

1. Click your [GitHub CodeSpaces container](https://github.com/codespaces).
1. Inside the online Visual Studio Code, look in the root folder for a `.env.copy` file that should have contents like this:

   ```bash
   ## Azure OpenAI
   AZURE_OPENAI_API_VERSION='2024-02-01' # Default is set!
   AZURE_OPENAI_API_KEY='<add your AOAI key here>'
   AZURE_OPENAI_ENDPOINT='<add your AOIA service endpoint here>'
   AZURE_OPENAI_DEPLOYMENT='<add your chat completion model name here>' 
   AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='<add your embeddings model name here>'
   ```

1. Copy that file to `.env` using the command below. This file is _gitignore-d_, keeping secrets safe.

Open the Codespaces Visual Studio Code **Terminal** and execute the following command:

   ```bash
   cp .env.copy .env
   ```

1. Fill in the values (replace placeholders on right side of `=`) as described in the next section.

> [!NOTE]
> If you use GitHub Codespaces, you have the option to save environment variables as **Codespaces secrets** associated with this repository.
> In that case, you won't need to setup a local `.env` file.
> **Note that this option works only if you use GitHub Codespaces.**
>
> [!NOTE]
> You will still need to setup the `.env` file if you use your local Visual Studio Code tool.

### 2.2. Populate `.env` file

Let's take a quick look at the variable names to understand what they represent:

| Variable  | Description  |
| :--- | :--- |
| AZURE_OPENAI_API_KEY | This is the authorization key for using that service |
| AZURE_OPENAI_ENDPOINT | This is the deployed endpoint for an Azure OpenAI resource |
| AZURE_OPENAI_DEPLOYMENT | This is the _text generation_ model deployment endpoint |
| AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT | This is the _text embeddings_ model deployment endpoint |
| | |

> [!NOTE]  
> The last two Azure OpenAI variables reflect a default model for chat completion (text generation) and vector search (embeddings) respectively.
> Instructions for setting them will be defined in relevant assignments.

### 2.3 Get Azure OpenAI access values: From Portal

The Azure OpenAI endpoint and key values will be found in the [Azure Portal](https://portal.azure.com) so let's start there.

1. Go to the [Azure Portal](https://portal.azure.com).
1. Go to the Azure OpenAI resource.
1. Expand the **Resource Management** section in the sidebar (menu at left)
1. Click the **Keys and Endpoint** option.
1. Click **Show Keys** - you should see the following: KEY 1, KEY 2 and Endpoint.
1. Use the **KEY 1** value for **AZURE_OPENAI_API_KEY**.
1. Use the **Endpoint** value for **AZURE_OPENAI_ENDPOINT**.

Next, we need to create deployments from the Azure OpenAI models.

1. Click the **Model deployments** option in the sidebar (left menu) for Azure OpenAI resource.
1. In the destination page, click **Manage Deployments**
1. (Optional) You can directly navigate to the [Azure OpenAI Studio website](https://oai.azure.com).

This will take you to the Azure OpenAI Studio website, where we'll find the other values as described below.

### 2.4 Get Azure OpenAI deployments: From Studio

1. Navigate to [Azure OpenAI Studio](https://oai.azure.com) **from your resource** as described above.
1. Click the **Deployments** tab (sidebar, left) to view currently deployed models.
1. If your desired model is not deployed, use **Create new deployment** to deploy it. If using the new portal, use **Deploy model** button.
1. You will need a _text-generation_ model - we recommend: **gpt-4**
1. You will need a _text-embedding_ model - we recommend **text-embedding-ada-002**

Now update the environment variables from the `.env` file to reflect the **Deployment name** used from above. This will typically be the same as the model name unless you changed it explicitly. So, as an example, you might have:

```bash
AZURE_OPENAI_DEPLOYMENT='gpt-4'
AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='text-embedding-ada-002'
```

**Don't forget to save the .env file when done**. You can now exit the file and return to the instructions for running the notebook.

## Let's Get Started

Now that you have completed the needed steps to complete this course, let's get started with the [laboratories](../01-laboratories/README.md).

> [!NOTE]
> This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information read the Code of Conduct FAQ or contact [Email opencode](opencode@microsoft.com) with any additional questions or comments.
