---
title: Gabe Busto
layout: page
---

## quick intro
i'm gabe, a builder at heart with a broad, generalized skill set. over the last few years i've been exploring different ways of creating things on my own, from testing business models to building and launching ai tools. that path eventually led me to [blocksmith ai](https://blocksmithai.com), my first "real" product that combines applied ai with game development. (technical writeup can be found [here](./blocksmithai.md))

i'm now looking to join a company working with ai, ideally as an applied ai or research engineer. my focus is on growing into a builder without limits: able to move fluidly between raw research, published code, open-weight models, and production systems, and build products that have a big impact and provide tons of value.


## socials
- X - [@gabebusto](https://x.com/gabebusto)
- LinkedIn - [@gabrielbusto](https://linkedin.com/in/gabrielbusto)
- Github - [@gbusto](https://github.com/gbusto)


## posts / technical writeups
- [blocksmith ai](./blocksmithai.md) - technical writeup
- [helpful resources](./resources.md) - a collection of helpful resources
- [(oct 9 2025) speed models](./posts/oct-9-2025-speech-models.md) - a quick writeup of a demo app playing with voice cloning via IVR, and a new speech model that can do true speech-to-speech
- [(oct 6 2025) omniflow](./posts/oct-6-2025-omniflow.md) - an open source tool to make data transformation, cleaning, and prep easier prior to training and fine tuning


## projects / apps
[see my projects and apps](./projects.md)


### game building experience
[see games i've built](./games.md)


## previous work experience
[see my work experience](./experience.md)


## currently working on:
- reading [*neural networks from scratch*](https://nnfs.io/)

- improving blocksmithai.com:
    - improving model generation; don't have a ton of raw data, so exploring fine tuning options vs a simple rag-like approach to pull exemplars from different model classes
    - improving blocksmith texturing
        - one option is to update mv-adapter to use sd3.5 instead of sdxl. sd3.5 is just so much better
        - another option is to figure out how to fine tune / train mv-adapter to have a fixed understanding of north/south/east/west. untextured block models are vague, and it's hard to know what side is actually the front or back of a model. if i could find someway for it to understand one camera angle as "front" or north consistently, it could solve a lot of headaches.
        - if i can get sd3.5 working with mv-adapter, create a fine-tuned version for outputting minecraft/hytopia style game asset concept images
    - updating blocksmith ux to more of a workflow than a conveyer belt
        - work in a single ui view where you can generate a concept image, use that to generate a model, edit via prompt, then texture
            - this type of ux is what's necessary to make it a good experience to add animation support finally
