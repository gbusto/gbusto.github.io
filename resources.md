---
title: Useful Resources, Tools, Platforms
layout: page
---

## summary
this is a page i wanted to put together with a list of project ideas, resources, platforms, tools, etc that i've come across in case it's helpful to others. i'll likely exclude really obvious sites and tools like chatgpt, claude, etc.


## table of contents
- [books](#books)
- [videos](#videos--channels)
- [project ideas](#project-ideas)
- sites and platforms
- repositories


### books
- [Neural Networks from Scratch](https://nnfs.io/) - a book that is exactly what it sounds like. learn to build neural networks from scratch using pure python.
- [Deep Learning with Python](https://deeplearningwithpython.io/) - haven't bought this book, but it looks like a great resource


### videos / channels
- [3Blue1Brown](https://www.youtube.com/@3blue1brown) - amazing educational videos related to math and similar topics
    - [Deep Learning / Nueral Networks Playlist](https://www.youtube.com/watch?v=aircAruvnKk&list=PLZHQObOWTQDNU6R1_67000Dx_ZCJB-3pi) - an awesome intro to neural networks and deep learning, and even covers llms and transformers


### project ideas
a collection of ideas and things to explore to get hands on experience. i'm a bit sparse on the details for now, but will improve this list over time.

- get a very small model running on your own local machine
    - you could use [ollama](https://ollama.com/), but trying going to huggingface and finding a very small model that is <= 1B params and use the provided example code
- train a small model on your machine; you can use [Unsloth](https://docs.unsloth.ai/new/how-to-train-llms-with-unsloth-and-docker)
- same as the above two, but try running and/or training a larger model on a platform like [Modal](https://modal.com/)
- after getting a model running with a very simple setup (especially a larger one on modal) use vllm for hosting that model and compare how much faster it is. they have a [guide for using vllm on modal](https://modal.com/docs/examples/vllm_inference)
- get an open source/weights image gen model running locally or remotely
    - explore options to speed up inference/diffusion
- get an open source/weights audio/speech model running locally or remotely
    - explore options to speed up inference/diffusion
- build a really simple app using a cool new model like Gemini's [Nano Banana](https://gemini.google/overview/image-generation/)
- get an old school state of the art model running; [gpt-2](https://github.com/openai/gpt-2) and [grok-2](https://huggingface.co/xai-org/grok-2) are the first ones that come to mind
- train your own small neural network from scratch


### sites and platforms
there are SO many. too many to list. but i'll try and keep it up to date as i remember / learn about more.

- [Modal](https://modal.com) - write python code on your machine, and run it remotely on their gpus.
    - they have some cool educational resources. they have lots of [examples](https://modal.com/docs/examples) for what you can do on modal, a well written [guide](https://modal.com/docs/guide) on how to use their platform, and a [gpu glossary](https://modal.com/gpu-glossary)
- [Hugging Face 🤗](https://huggingface.co/) - *the* ai community. think of it like github, but for ai and ai models.
    - companies and individual upload their latest models (literally every kind you can imagine), fine tunes, data sets for training, etc. they also provide infrastructure to deploy and manage your own models and fine tuning. probably one of the best resources out there
- [Unsloth](https://unsloth.ai/) - an open source framework for llm fine-tuning and reinforcement learning; they try to make it faster and easier.
    - they're also a great learning source on top of their tooling to help speed up model training with lots of guides
- [Replicate](https://replicate.com) - tons of hosted models (and even fine-tunes) that you can run from an api with pay-as-you pricing easily.
    - i think they focus more on image/video models, but they do have some llms on there. you can even do finetuning on there, and deploy your own custom models
- [Fal](https://fal.ai/) - in my mind, this is basically just a competitor of Replicate and they offer the ~same exact thing as far as i can tell (not a bad thing!)
- [Elevenlabs](https://elevenlabs.io/) - an audio ai platform; text to speech (TTS), speech to text (STT), realtime speech, voice cloning, sound effects, music, dubbing, etc
- [AssemblyAI](https://www.assemblyai.com/) - focused entirely (at least they used to be) on speech to text.
    - they provide amazing state of the art models for fast, cheap, and highly accurate transcription. including fancy features like diarization and recognizing multiple speakers, extracting insights from text, and even more advanced features like filtering out PII.
- [arxiv](https://arxiv.org/) - the place where it seems like every paper for ai/ml/math gets published. anytime you see someone talking about a new paper, they're likely linking to it on arxiv.
- [Luma Labs](https://lumalabs.ai/) - a frontier multimodal (primarily video?) lab.
    - they have image generator models, video generator models, and even a 3d model generator
    - they recently released their new state of the art video model: [Ray3](https://lumalabs.ai/ray)
        - it is STUNNING. and it's an incredibly cool architecture that is capable of **thinking and reasoning** in visuals. they have some really neat capabilities too.
- [Meshy](https://www.meshy.ai/) - a 3d model generator; competes with models like Hunyuan 3d. seems really solid though, and they have a nice interface.
- [Factory AI](https://factory.ai/) - agent-native software development. their agents are called Droids. don't know much about it, but it looks cool!
- [Thinking Machines](https://thinkingmachines.ai/) - a new lab started by the former cto of openai (Mira Murati).
    - they have a blog with some posts on it; they will likely continue to put out great blog posts
    - just released their first product: [Tinker](https://thinkingmachines.ai/tinker/). it's a training api; sounds nice, but in my opinion not all that different than what modal offers. i get the impression it will be a bit more "done for you" than what modal offers.
- [Together AI](https://www.together.ai/) - i'm not super clear on what this is, but it seems like a platform to train and host open source models with production-level infrastructure
- [Fireworks AI](https://fireworks.ai/) - i think it's ~similar to Together AI. one notable thing about these guys though is that their platform emphasized privacy, and are even HIPPA compliant!
- [Comfy](https://www.comfy.org/) - an open source, node-baesd app for genai. they have a desktop app you can use to run it locally. i hear a lot about it but have never used it personally
- [Weavy](https://www.weavy.ai/) - a powerful artistic tool that lets you build custom and complex flows with text, image, and video gen models
- [Weaviate](https://weaviate.io/) - not to be confused with Weavy! they provide a RAG database service, and also have an open source implementation
- [Unstructured](https://unstructured.io/) - helps you transform complex and unstructured data into structured data; i've used it before for their advanced chunking strategies prior to saving a RAG database.