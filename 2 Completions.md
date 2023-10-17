# Completions

In this section, you will experiment with creating completions with OpenAI natural language models. We will use the GPT-3.5 model `gpt-35-turbo` throughout this section.

## What is a completion?

A natural language model like OpenAI's `gpt-35-turbo` has a simple purpose: Given a fragment of text (the "prompt"), generate additional text that is likely to follow the prompt. This is called a "completion".

The definition of "likely" is more complex, but for now, you can think of it as "text similar to text in the training data that often follows text like the prompt". Models like `gpt-35-turbo` are trained on very large volumes of text data from the internet, and this data influences the model's predictions.

You can learn more details about how OpenAI's models work at Microsoft Learn: [Understand OpenAI's natural language capabilities](https://learn.microsoft.com/en-us/training/modules/explore-azure-openai/5-understand-openai-natural-language).

## Launch the Completions Playground

In the left navigation of the Azure OpenAI Studio home page, click "Completions" under the "Playground" heading.

In the drop-downs under "Completions playground" make sure the following options are selected:

1. Deployments: `gpt-35-turbo`
2. Examples: `Load an example` (do not change this option yet)

## Basic Prompting

In the prompt box (where you see the text "Start typing here"), you can enter any text you like, and then use one of your deployed models to generate a completion. Let's try a few examples.

By default, the Completions Playground limits the length of completions to 100 tokens (about 75 words). To allow for longer completions, change the "Max tokens" option in the right column from 100 to 1000.

Here are some examples to try, but get creative with your own prompts and see what happens!

```
What is the capital of Australia? Give me a fun fact about this city.
```
```
A recipe for banana bread, and an itemized shopping list of the ingredients.
```
```
What were the 10 top movies of 2001? Respond in the form of a table listing the movie name, the box office earnings, and the studio.
```


## Load an example

The Completions playground has a variety of example scenarios already preloaded. Load an example and try it out.

Feel free to try:
```
Generate an email
```
```
Translate text
```
```
Generate product name ideas
```





**Make sure the Temperature parameter is reset to 1 before you continue.**

## Less-useful prompts

Natural language generative AI models have a number of limitations:

* They are limited by their training data, which was frozen at a fixed point in time in the past.
* They generate text that resembles human language, but are not capable of reasoning or cognition.
* They have no memory of prior prompts, and no capability to learn or change their behavior.

Here are some example prompts that demonstrate these weaknesses:

    When is NYC tech week 2023?

In this case, the model is limited by training data, which is current only up to September 2021.

    What is the square root of 98765?

The model will generate an answer to math questions, but there's no guarantee it will be correct. (If it is correct, it's only because the question and answer are represented in the training data.)

But you could ask the model to write Python code to calculate the square root of 98765, and it would probably do a good job. (Try it!).

    Write Python code to calculate the square root of 98765



In the following section, we'll explore other aspects of completions.

## Generative AI models have a limited memory

If you navigate into the Configuration side panel in the Chat playground you will see a "Past messages included" option. This option controls how much of the conversation is included in the prompt. The default value is 10, which means that the prompt includes the past 10 messages in the conversation. However, when a new session is created (by reloading the page for example), the conversation history is cleared.

## Generative AI models can't perform actions

Clear the contents of the prompt box. Enter the following text, then click Generate.

    What are the 5 stocks listed on https://finance.yahoo.com/trending-tickers with the largest market cap?

Although the model will respond with a plausible answer, look closely: those aren't *actually* the 5 largest stocks on the list. Foundational AI models are not capable of performing actions, so they can't actually visit the web page and read the list of stocks. Instead, they generate a plausible response based on the prompt and the training data.

*Note, there are cutting edge models that can complete actions like perform API calls and search the internet*

## Completions are not facts

Clear the contents of the prompt box. Enter the following text, then click Generate.

    Write an obituary for the poet Harold Bloomsbury. Include references.

There has never been a poet (nor indeed any person, according to web search) named Harold Bloomsbury. As a result, the model generates text in the form of an obituary, but not grounded in any facts. Even the requested references, while convincing-looking, are not real.

## Next Steps

Now, proceed to [3 Using Your Data.md](https://github.com/e-straight/OAI-Demo/blob/main/3%20Using%20Your%20Data.md).
