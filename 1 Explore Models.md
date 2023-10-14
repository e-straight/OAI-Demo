# Explore Models

Before you begin this section, navigate to your Azure OpenAI Studio homepage:

1. In the Azure Portal, click on the Azure OpenAI resource `openai-lab-build`
2. Click the "Explore" button to open the Azure OpenAI Studio

Remember, you chose your own unique name to replace `openai-lab-build` above. During this workshop you will often need to return to the home page of the Azure OpenAI Studio, so refer back to this section if you need a reminder of how to get there.

## Your deployed models

Click on **Deployments** in the "Management" section of the left pane. You have two models deployed:

* `gpt-35-turbo`: "Most capable GPT-3.5 model and optimized for chat at 1/10th the cost of text-davinci-003." -[OpenAI](https://platform.openai.com/docs/models/gpt-3-5)
* `text-embedding-ada-002`: "Embeddings are a numerical representation of text that can be used to measure the relatedness between two pieces of text. text-embedding-ada-002 is a designed to replace the previous 16 first-generation embedding models at a fraction of the cost." -[OpenAI](https://platform.openai.com/docs/models/embeddings)

In this workshop, we will occasionally mention GPT-4, the latest model from OpenAI, but we will not deploy it.

You can find details about these models and other models available in Azure OpenAI Service at [https://aka.ms/oai/models](https://aka.ms/oai/models).

## Which model should I use?

There are many considerations when choosing a model, including cost, availability, performance, and capability. But as a general guide, we recommend the following:

* Start with `gpt-35-turbo`. This model is very economical, has good performance, and despite the "ChatGPT" name can be used for a wide range of tasks beyond chat and conversation.

* If you need to generate more than 4,096 tokens, or need to support larger prompts, you will need to use `gpt-4` or `gpt-4-32k`. These models are more expensive and can be slower, and have limited availability, but they are the most powerful models available today.

* `text-embedding-ada-002` is widely considered one of the best text embedding models on the market today. It is also extremely economical, with pricing currently sitting at $0.0001/1K tokens.

## Next steps

Return to the Azure OpenAI Studio home page by clicking "🏠 Azure OpenAI" in the left-hand column.

Now, proceed to [2 Completions.md](https://github.com/e-straight/OAI-Demo/blob/main/2%20Completions.md)
