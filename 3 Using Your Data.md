# Using Your Data

In this section, you will experiment with  grounding a chatbot with your own data.

## Why would we want to ground our model?

While the capabilities of LLMs appears to be endless, they are limited to the data they were trained on. This means that they are only accurate to a specific point in time. GPT4, for example, is only accurate through September of 2021. However, using a technique called Retrieval Augmented Generation (RAG) we are able to expand the power of these models by grounding the model in our data. To learn more about RAG check out this [link](https://learn.microsoft.com/en-us/azure/machine-learning/concept-retrieval-augmented-generation?view=azureml-api-2).



## Observe normal chat behavior without adding your own data
Before connecting Azure OpenAI to your data, first observe how the base model responds to queries without any grounding data.

1. Navigate to the Chat playground, and make sure the gpt-35-turbo model you deployed is selected in the Configuration pane (this should be the default).
2. Enter the following prompts, and observe the output.

 ```
 I'd like to take a trip to New York. Where should I stay?
 ```

```
What are some facts about New York?
```

3. Try similar questions about tourism and places to stay for other locations that will be included in our grounding data, such as London, or San Francisco. You’ll likely get complete responses about areas or neighborhoods, and some general facts about the city.

## Connect your data in the chat playground
Next, add your data in the chat playground to see how it responds with your data as grounding

1. [Download the data](https://aka.ms/own-data-brochures) that you will use from GitHub. Extract the PDFs in the .zip provided.
2. Navigate to the **Chat** playground, and select Add your data in the Assistant setup pane.
3. Select **Add a data source** and choose Upload files from the dropdown.
4. You’ll need to create a storage account and Azure Cognitive Search resource. Under the dropdown for the storage resource, select **Create a new Azure Blob storage resource**, and create a storage account with the following settings. Anything not specified leave as the default. Azure Blob Storage is a scalable and secure object storage for cloud-native workloads, archives, data lakes, high-performance computing, and machine learning. [Learn more here](https://azure.microsoft.com/en-us/products/storage/blobs/).

- **Subscription**: Same subscription as your Azure OpenAI resource
- **Resource group**: Same resource group as your Azure OpenAI resource
- **Storage account name**: Enter globally unique name
- **Region**: Same region as your Azure OpenAI resource
- **Performance**: Standard
- **Redundancy**: Geo-zone-redundant storage (GZRS)

5. Once the resource is being created, come back to Azure OpenAI Studio and select Create a new Azure Cognitive Search resource with the following settings. Anything not specified leave as the default. Azure Cognitive Search is an AI-powered information retrieval platform, helps developers build rich search experiences and generative AI apps that combine large language models with enterprise data. [Learn more here](https://azure.microsoft.com/en-us/products/ai-services/cognitive-search).

- **Subscription**: Same subscription as your Azure OpenAI resource
- **Resource group**: Same resource group as your Azure OpenAI resource
- **Service name**: Enter globally unique name
- **Location**: Same location as your Azure OpenAI resource
- **Pricing tier**: Basic

6. Wait until your search resource has been deployed, then switch back to the Azure AI Studio and refresh the page.
7. In the **Add data**, enter the following values for your data source, then select **Next**.

- **Select data source**: Upload files
- **Select Azure Blob storage resource**: Choose the storage resource you created
    - Turn on CORS when prompted
- **Select Azure Cognitive Search resource**: Choose the search resource you created
- **Enter the index name**: margiestravel
- **Add vector search to this search resource**: unchecked
- **I acknowledge that connecting to an Azure Cognitive Search account will incur usage to my account**: checked

8. On the **Upload files** page, upload the PDFs you downloaded, and then select Next.
9. On the **Data management** page select the Keyword search type from the drop-down, and then select Next.
10. On the **Review and finish** page select **Save and close**, which will add your data. This may take a few minutes, during which you need to leave your window open. Once complete, you’ll see the data source, search resource, and index specified in the **Assistant setup** pane.

## Chat with a model grounded in your data
Now that you’ve added your data, ask the same questions as you did previously, and see how the response differs.


```
I'd like to take a trip to New York. Where should I stay?
```

```
What are some facts about New York?
```

You’ll notice a very different response this time, with specifics about certain hotels and a mention of Margie’s Travel, as well as references to where the information provided came from. If you open the PDF reference listed in the response, you’ll see the same hotels as the model provided.

Try asking it about other cities included in the grounding data, which are Dubai, Las Vegas, London, and San Francisco.

Not only can customers of Margie's Travel use this chatbot, but so can Margie's employees. Try asking the question:

```
Can you generate a 1 paragraph email ad for me about Margie's Travel?
```
## System Message
The System Message "gives the model instructions about how it should behave and any context it should reference when generating a response. You can describe the assistant’s personality, tell it what it should and shouldn’t answer, and tell it how to format responses. There’s no token limit for this section, but it will be included with every API call, so it counts against the overall token limit."

This allows the user to further engineer how the model will respond to prompts.

## Clean up
When you’re done with your Azure OpenAI resource, remember to delete the resource in the Azure portal. Be sure to also include the storage account and search resource, as those can incur a relatively large cost.

Now, proceed to [4 DALL-E.md](https://github.com/e-straight/OAI-Demo/blob/main/4%20DALL-E.md).