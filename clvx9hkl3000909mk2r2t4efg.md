---
title: "Create Your Own AI ChatBot using Llama3 by meta"
seoTitle: "Your AI Text To Text Genai"
seoDescription: "You can have your chatbot just like chatGPT"
datePublished: Wed May 08 2024 03:30:18 GMT+0000 (Coordinated Universal Time)
cuid: clvx9hkl3000909mk2r2t4efg
slug: llama3
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1715104048514/353e18da-475e-48be-9472-b4a5f458eda1.png
ogImage: https://cdn.hashnode.com/res/hashnode/image/upload/v1715104208066/1a4c7c73-2c4d-44a3-a6aa-e6e065c6b402.png
tags: tutorial, ai, community, chatbot, chatbots, ai-tools, generative-ai, chatgpt, aitools, llama, llama2, genai, ollama, genai-applications, llama3

---

On May 3rd, 2024, the world experienced a collective moment of panic as ChatGPT and Gemini, two of the most widely used AI language models, went down for over two hours. This outage served as a stark reminder of how deeply we have become reliant on these generative AI (GenAI) tools in our daily lives and work.

As we scrambled to find alternative solutions, many of us were left feeling frustrated and helpless. It was during this time that I remembered the recent release of Llama 3, an open-source large language model developed by Meta. Unlike the proprietary models of ChatGPT and Gemini, Llama 3 can be run locally on your computer, providing a level of independence and control that is increasingly valuable in our rapidly evolving technological landscape.

# Prerequisite

Some things need to be installed on your computer

1. node
    
2. npm
    

# Llama3

Meta releasing their LLM open source is a net benefit for the tech community at large, and their permissive license allows most medium and small businesses to use their LLMs with little to no restrictions (within the bounds of the law, of course). Their latest release is Llama 3, which has been highly anticipated.

Llama 3 comes in two sizes: 8 billion and 70 billion parameters. This kind of model is trained on a massive amount of text data and can be used for a variety of tasks, including generating text, translating languages, writing different kinds of creative content, and answering your questions in an informative way. Meta touts Llama 3 as one of the best open models available, but it is still under development. Here are the 8B model benchmarks when compared to Mistral and Gemma (according to Meta).

![Benchmarks](https://media.dev.to/cdn-cgi/image/width=800%2Cheight=%2Cfit=scale-down%2Cgravity=auto%2Cformat=auto/https%3A%2F%2Fdev-to-uploads.s3.amazonaws.com%2Fuploads%2Farticles%2Fax9r9z2w2zghv81grbh7.png align="left")

This begs the question: how can I, the regular individual, run these models locally on my computer?

## Getting Started with Ollama

That’s where [Ollama](https://ollama.com/) comes in! Ollama is a free and open-source application that allows you to run various large language models, including Llama 3, on your own computer, even with limited resources. Ollama takes advantage of the performance gains of llama.cpp, an open-source library designed to allow you to run LLMs locally with relatively low hardware requirements. It also includes a sort of package manager, allowing you to download and use LLMs quickly and effectively with just a single command.

The first step is [installing Ollama](https://ollama.com/download). It supports all 3 of the major OS.

Once this is installed, open up your terminal. On all platforms, the command is the same.

```basic
ollama run llama3
```

Wait a few minutes while it downloads and loads the model, and then start chatting! It should bring you to a chat prompt similar to this one.

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714841851047/b77de6d7-e421-4ff8-b5cb-0d1a91693c3d.png align="center")

You can chat all day within this terminal chat, but what if you want something more ChatGPT-like?

# ChatBot WebUI

First, we have to clone this repo [**chatbot-ollama**](https://github.com/ivanfioravanti/chatbot-ollama) in your local machine, You can use this command to so do

```basic
git clone https://github.com/ivanfioravanti/chatbot-ollama.git
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714891798140/843925df-ab85-4675-a45e-b040a86852c6.png align="center")

Now cd in that repo and install all packages with this command

```basic
npm ci
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714892134855/dc988186-126d-4c82-a449-7b26a0d3a860.png align="center")

Now we have to create `.env` a file where will we scarify your public IP where Ollama is running with the llama3 model.

```basic
# Chatbot Ollama
DEFAULT_MODEL="mistral:latest"
NEXT_PUBLIC_DEFAULT_SYSTEM_PROMPT=""
OLLAMA_HOST="http://0.0.0.0:11434"
```

Paste this code in your `.env` file in the root folder.

Now every everything is set let's start the Chatbot application by just running these commands.

```basic
npm run dev
```

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714893310949/4410a0e1-701e-412c-84e5-29a5408e1b23.png align="center")

It will take fu sec to start then you visit on `localhost:3000`

> make sure there is no other application running on that port

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1714893692709/83843b34-8a9a-4f51-b4db-64b522138d04.png align="center")

Nice!!! As you can see now you have your ai chatbot just like ChatGPT.

## For GPU User

So I'm running on my Mac laptop, but if you have a PC with a powerful Nvidia GPU or AMD GPU, I highly recommend downloading the Llama3 with 70 billion parameters. Which is a much faster and much better answer.

You have to run this command.

```basic
ollama run llama3:8b
```

The model file will be 40GB which will take time to download but will work way better than the model with 4GB.

## Conclusion

The ability to run powerful AI models locally has become increasingly valuable. With Ollama and Llama 3, you can ensure that you have access to the tools you need, whenever you need them, without being at the mercy of external service providers.