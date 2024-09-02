# Setup Your Dev Environment

After setting up the [working environment](./README.md), it is time to configure specific items to make the code work.

## 1. Executing Assignments

This section provides general guidance related to executing those assignments.

### 1.1. Python Assignments

Python assignments are provided either as applications (`.py` files) or Jupyter notebooks (`.ipynb` files).

* To run the notebook, open it in Github Codespaces Visual Studio Code, then click **Select Kernel** (at top right) and select the default **Python** option shown. You can now **Run All** to execute the whole notebook.
* To run Python applications from command-line, follow assignment-specific instructions to ensure you select the right files and provide required arguments.

## 2. Configuring Providers

Assignments **may** also be setup to work against one or more Large Language Model (LLM) deployments through a supported service provider like Azure OpenAI or Hugging Face. This provides a **hosted endpoint** (API) that we can access programmatically with the right credentials (API key or token). In this course, we discuss these providers:

* [Azure OpenAI](https://learn.microsoft.com/azure/ai-services/openai/) for OpenAI models with enterprise readiness in focus.
* [Hugging Face](https://huggingface.co/docs/hub/index) for open-source models and inference server.

**You will need to use your own accounts for these exercises**. Some guidance for signup:

| Signup | Cost | API Key | Playground | Comments |
|:---|:---|:---|:---|:---|
| [Azure](https://aka.ms/azure/free)| [Pricing](https://azure.microsoft.com/pricing/details/cognitive-services/openai-service/)| [SDK Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart)| [Studio Quickstart](https://learn.microsoft.com/azure/ai-services/openai/quickstart) |  [Must Apply Ahead For Access](https://learn.microsoft.com/azure/ai-services/openai/)|
| [Hugging Face](https://huggingface.co/join) | [Pricing](https://huggingface.co/pricing) | [Access Tokens](https://huggingface.co/docs/hub/security-tokens) | [Hugging Chat](https://huggingface.co/chat/)| [Hugging Chat has limited models](https://huggingface.co/chat/models) |
| | | | | |

Follow the directions below to **configure** this repository for use with different providers. Assignments that require a specific provider will contain one of these tags in their filename:

* `aoai` - requires Azure OpenAI endpoint, key and deployment name
* `hf` - requires Hugging Face token

You can configure one, none, or all providers. Assignments will simply error out on missing credentials.

### 2.1. Create `.env` file

We assume that you have already read the guidance above, signed up with the relevant provider, and obtained the required authentication credentials (API_KEY or token). In the case of Azure OpenAI, we assume you also have a valid deployment of an Azure OpenAI Service (endpoint) with at least one GPT model deployed for chat completion.

The next step is to configure your **local environment variables** as follows:

1. Look in the root folder for a `.env.copy` file that should have contents like this:

   ```bash
   ## Azure OpenAI
   AZURE_OPENAI_API_VERSION='2024-02-01' # Default is set!
   AZURE_OPENAI_API_KEY='<add your AOAI key here>'
   AZURE_OPENAI_ENDPOINT='<add your AOIA service endpoint here>'
   AZURE_OPENAI_DEPLOYMENT='<add your chat completion model name here>' 
   AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='<add your embeddings model name here>'

   ## Hugging Face
   HUGGING_FACE_API_KEY='<add your HuggingFace API or token here>'
   ```

1. Copy that file to `.env` using the command below. This file is _gitignore-d_, keeping secrets safe.

Open the Codespaces Visual Studio Code **Terminal** and execute the following command:

   ```bash
   cp .env.copy .env
   ```

1. Fill in the values (replace placeholders on right side of `=`) as described in the next section.

1. (Option) If you use GitHub Codespaces, you have the option to save environment variables as **Codespaces secrets** associated with this repository. In that case, you won't need to setup a local `.env` file. **However, note that this option works only if you use GitHub Codespaces.** You will still need to setup the `.env` file if you use Docker Desktop instead.

### 2.2. Populate `.env` file

Let's take a quick look at the variable names to understand what they represent:

| Variable  | Description  |
| :--- | :--- |
| AZURE_OPENAI_KEY | This is the authorization key for using that service |
| AZURE_OPENAI_ENDPOINT | This is the deployed endpoint for an Azure OpenAI resource |
| AZURE_OPENAI_DEPLOYMENT | This is the _text generation_ model deployment endpoint |
| AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT | This is the _text embeddings_ model deployment endpoint |
| HUGGING_FACE_API_KEY | This is the user access token you setup in your profile |
| | |

> [!NOTE]  
> The last two Azure OpenAI variables reflect a default model for chat completion (text generation) and vector search (embeddings) respectively.
>Instructions for setting them will be defined in relevant assignments.

### 2.3 Configure Azure: From Portal

The Azure OpenAI endpoint and key values will be found in the [Azure Portal](https://portal.azure.com) so let's start there.

1. Go to the [Azure Portal](https://portal.azure.com).
1. Click the **Keys and Endpoint** option in the sidebar (menu at left).
1. Click **Show Keys** - you should see the following: KEY 1, KEY 2 and Endpoint.
1. Use the **KEY 1** value for **AZURE_OPENAI_KEY**.
1. Use the **Endpoint** value for **AZURE_OPENAI_ENDPOINT**.

Next, we need the endpoints for the specific models we've deployed.

1. Click the **Model deployments** option in the sidebar (left menu) for Azure OpenAI resource.
1. In the destination page, click **Manage Deployments**

This will take you to the Azure OpenAI Studio website, where we'll find the other values as described below.

### 2.4 Configure Azure: From Studio

1. Navigate to [Azure OpenAI Studio](https://oai.azure.com) **from your resource** as described above.
1. Click the **Deployments** tab (sidebar, left) to view currently deployed models.
1. If your desired model is not deployed, use **Create new deployment** to deploy it.
1. You will need a _text-generation_ model - we recommend: **gpt-35-turbo**
1. You will need a _text-embedding_ model - we recommend **text-embedding-ada-002**

> [!WARNING]  
> VALIDATE THE _text-generation_ model TO USE BEFORE SENDING THIS TO PRODUCTION. REMOVE THIS WARNING AFTER DEFINED.

Now update the environment variables to reflect the **Deployment name** used. This will typically be the same as the model name unless you changed it explcitly. So, as an example, you might have:

```bash
AZURE_OPENAI_DEPLOYMENT='gpt-35-turbo'
AZURE_OPENAI_EMBEDDINGS_DEPLOYMENT='text-embedding-ada-002'
```

> [!WARNING]  
> VALIDATE THE _gpt-35-turbo_ DEPLOYMENT TO USE BEFORE SENDING THIS TO PRODUCTION. REMOVE THIS WARNING AFTER DEFINED.

**Don't forget to save the .env file when done**. You can now exit the file and return to the instructions for running the notebook.

### 2.5 Configure Hugging Face: From Profile

Your Hugging Face token can be found in your profile under [Access Tokens](https://huggingface.co/settings/tokens). Don't post or share these publicly. Instead, create a new token for this project usage and copy that into the `.env` file under the `HUGGING_FACE_API_KEY` variable. 

> [!NOTE]  
> This is technically not an API key but is used for authentication so we are keeping that naming convention for consistency.

## Let's Get Started

Now that you have completed the needed steps to complete this course, let's get started with the [laboratories](../01-laboratories/README.md).

> [!NOTE]
> This project has adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/). For more information read the Code of Conduct FAQ or contact [Email opencode](opencode@microsoft.com) with any additional questions or comments.
