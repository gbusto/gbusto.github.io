# omniflow

([Repo can be found here](https://github.com/gbusto/omniflow))

recently, Thinking Machines released a private beta of their [Tinker product](https://thinkingmachines.ai/tinker/). it seems neat, and i'm sure there's more to it what i'm seeing as an outsider, but it really doesn't seem that much different than what [Modal](https://modal.com) offers. it's maybe one layer "above" that with some niceties to handle scaling for training very large models. Modal has a max 50 concurrent gpu limit for their highest tier paid plan, below Enterprise, which may or may not be enough for fine tuning really large models.

but i saw lots of people mentioning they still have to deal with data collection, curation, transforming, cleaning, etc prior to training. based on own experiences, the pre-training part is actually more of a pain point in my opinion than actually running a training/fine-tuning job.

throughout my time building blocksmith, i went through SO MUCH trial and error of self hosting and running 3d diffusion models on Modal like hunyuan, trellis, paint3d, stepfun1x-3d, and others. i was trying to do everything i could to not reinvent the wheel if i could use something that was already ~state of the art, but none of them worked out for me. what i *did* find though is that many of them contained their own helper scripts for:
- fine tuning
- inference/diffusion
- evaluating model output after training, or cleaning data before training

i didn't think much of it until recently, and recalled my own pain of generating custom scripts to prepare and clean data for my own experimental training runs.

given that Tinker was coming out to make fine tuning easier, and people still seemed to have pain around pre-training steps of data collection and curation, i decided it might be worth it to create something new: *omniflow*.

the goal is simple: create a clean pipeline tool packed with tons of helpers for curating, cleaning, transforming, and preparing data for training runs. it needs to be really easy to use, flexible enough to create simple or powerful workflows to get data into the right form and shape that people need, and multi-modal.

it's limited right now because of what i've had time to integrate so far, but the idea is that you can ingest or start your pipeline in one modality, and output a completely different modality in the end.

i had one example from my own experience where i needed to take my dataset of 3d block models (think Minecraft), do off-screen rendering and take screenshots of them, ensure the screenshots are a certain size and have a consistent background color, etc. so start out with 3d models, and end up with screenshots. i had to write all of this code myself, but with omniflow, it would look something like this:
```py
    pipe = (
        Pipeline(source)
        .add(MeshTransformNormalizeMesh())
        .add(MeshScreenshots(elevation=args.el, azimuth=args.az, fov=args.fov, size=args.size, bg=None))
        .add(ImageTransformSetBackground(color=args.bg))
        .add(DestinationLocal(out_dir=args.out))
    )

    pipe.compile()
    pipe.run(print_summary=True)
```

i've started with 3d mesh and image helpers because these are definitely more scattered than others, but plan to support every modality:
- text
- audio (voice, sound, music)
- video
- 3d
- 2d
- others?

it also has first class support for huggingface datasets as a source, and can stream samples or download the entire dataset. i'll also eventually add support for writing *to* huggingface to create a new dataset.

it's available now, and i'll keep expanding it as quickly as i can. i'm also open to suggestions, improvements, and any help expanding its capabilities! i might decide to keep this 100% focused on data curation, but i see a lot of potential for a repo of tools that make it easy to (ethically!) source training data as well.

https://github.com/gbusto/omniflow