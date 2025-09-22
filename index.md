---
title: Gabe Busto
layout: page
---

## quick intro

i'm gabe, and i'm a builder at heart with a highly generalized skill set. over the last six months, i developed a deep interest in becoming something like an applied ai engineer or research engineer after building and launching what i would consider my first "real" ai product.

i basically want to be able to take my builder skills and mindset focus my time and energy on building really cool, novel, and actually useful ai products and tools; even if that means i need to leverage research that is currently just theory with no working code. i'm not at this point yet, but i'm taking steps to get there.


## currently working on:
- reading [*neural networks from scratch*](https://nnfs.io/); on chapter 5 at the moment

- improving blocksmithai.com:
    - improving model generation; don't have a ton of raw data, so exploring fine tuning options vs a simple rag-like approach to pull exemplars from different model classes
    - improving blocksmith texturing
        - one option is to update mv-adapter to use sd3.5 instead of sdxl. sd3.5 is just so much better
        - another option is to figure out how to fine tune / train mv-adapter to have a fixed understanding of north/south/east/west. untextured block models are vague, and it's hard to know what side is actually the front or back of a model. if i could find someway for it to understand one camera angle as "front" or north consistently, it could solve a lot of headaches.
        - if i can get sd3.5 working with mv-adapter, create a fine-tuned version for outputting minecraft/hytopia style game asset concept images
    - updating blocksmith ux to more of a workflow than a conveyer belt
        - work in a single ui view where you can generate a concept image, use that to generate a model, edit via prompt, then texture
            - this type of ux is what's necessary to make it a good experience to add animation support finally

- looking to join a company working with ai in some capacity; ideally as an applied ai engineer or ai research engineer type role


## projects / apps

most of these were full end-to-end apps that were deployed, had a signup flow, and database. some were just prototypes or for fun.


### blocksmith ai (3d block model generation)

(🚧 working on creating a new page to go into more detail about blocksmith, its progression, and the trial and error i went through)

this is the "real" ai product i mentioned above. by real, i mean it's more than just a gpt wrapper. it's a webapp that let's you create 3d block models (think minecraft) from a prompt. it also has the ability to texture them using the classic pixel art look that minecraft is known for.

you can actually visit the site and use the tool for free at https://blocksmithai.com. i created it to address major friction in the development of games on the hytopia game platform (think minecraft-meets-roblox), and currently have a few paying customers (including a team account using it to create models for their games). i've also had probably close to, if not more than, 100 free users over the last several months without putting any real effort into marketing because i was focused on building. i believe marketing gets easier once you know your product is amazing, and it's *almost* there.

i'll provide a technical writeup sharing some of the details of the application, experiments i ran, dead ends i ran into, etc. but going into this, i had zero experience in 3d, and zero experience with minecraft (aside from knowing that it existed, and that everything is blocky and pixelated).

but no other ai model, platform, or tool replicates what blocksmith can do. a big part of the reason is that the entire 3d ai space is focused on high-poly, watertight mesh generation. nothing out there can create a model made of multiple, perfect cuboidal parts, and then generate a pixelated texture for it. my model generation pipeline uses no outside dependencies like blockbench or blender to build the model, and uses [mv-adapter](https://github.com/huanngzh/MV-Adapter) (hosted on [modal](https://modal.com)) for multi-view consistent diffusion, then a custom backprojection pipeline to paint the mesh's original atlas and giving it that nice pixelated look and style.

i have the ability to animate these models using ai as well, but haven't integrated it into the site yet because the ux need some changes before it makes sense to add that in.

[latest texturing engine showcase](https://x.com/gabebusto/status/1966232224560279842)


### ai tutor (duolingo-like web app)

this was a webapp with a very simple interface. it was focused on helping people learn more about ai in byte-sized chunks (yes, pun intended), but there's no reason it couldn't have been opened up to learning anything about anything given the way it was developed.

you would sign up, have a short onboarding that shares your motivation and preferred learning style and tutor personality, and that's it. then enter a topic you want to learn about, and i would use ai to quickly research the topic to come up with high level modules + a description of why that was useful.

the user could click on a module, and ai would would then dive in and quickly research that module using the contextual description to create 5-10 screen-sized small lessons. lessons were just text, but included citations and sources.

at the end of the module, there are questions based on the lessons to test your knowledge. ai would dynamically generate these questions, and they could be a simple fill in the blank, multiple choice, or short answer. ai would grade your response and give you feedback if you got it wrong to help give you some feedback.

[app onboarding flow demo](https://x.com/gabebusto/status/1898053743746187356)

[module, lesson, and quiz demo](https://x.com/gabebusto/status/1899470710122205311)


### research paper assistant (prototype)

this was a prototype that i never launched publicly or posted about, but it led to the ai tutor app above. it came pre-loaded with ai research papers, and you could open them up onto an infinite canvas. you could move and re-arrange the pages however you wanted.

on any given pdf page, you could click and drag to create a highlight box, then right click to either create a sticky note for that region, or start a chat with ai about that region. it would clip the image behind the highlight box, and send it to an llm along with context about what paper you're reading and what page you're on.

each paper that was "pre-loaded" was processed using [unstructured.io's open source chunking code](https://github.com/Unstructured-IO/unstructured), and [weaviate](https://github.com/weaviate/weaviate) as a rag database to store the chunks. i used litellm on the server as the tool using assistant/agent, and it could:
- search the internet using google's search api
- query the weaviate rag database using several different methods (search across papers, for through a single paper, retrieve page contents, etc)

i planned to continue developing it, but thought the ai tutor path would make a better app. most people who read research papers may already use something like notebooklm, or not really feel the need to take notes or ask ai questions. folks who are newer to ai may not want to wade through research papers. so i made the shift to the ai tutor app.


### other random ai apps

- (a prototype) created a separate tool that could process a video (capture frames, align them with audio transcription from AssemblyAI, and batch process them), understand it, and then answer questions.

- (full web app) developed an app that uses ai to analyze the cohesiveness of a youtube video’s thumbnail, title, and first 30 seconds of audio. it used the youtube api to pull the transcript, title, and thumbnail, and litellm to have an llm generate scores and curate feedback.

- (full web app) built a landing page analysis tool that could dynamically load, screenshot, and parse page text to give users actionable feedback to improve conversions and reduce bounce rate.


### an nft art marketplace (full web app + android tv app + custom smart contracts)

in march/april of 2020 covid hit and locked everything down. i was living in arlington, va at the time working at raytheon doing computer security research. my job was in-person, so it was a really weird time, but my (now) wife and i wanted to get out of the city and dc area and move to raleigh. and i decided to leave my job at raytheon and to build an nft art marketplace, where my cousin (who was an artist) would be the business guy and use his network in the art world to help, and i would be the engineer that builds the app.

i had no experience at the time with aws, production apps and workflows, blockchain; nothing. i thought it was either going to be the dumbest thing i ever did, or one of the best. turns out it was somewhere in the middle, but leaning more towards the "good" side.

i quickly learned about ethereum smart contracts and how to build apps, picked django and python as our backend, aws as our infra for the app, and infura as our infra for blockchain. i learned pretty early on that nfts were basically pointless and couldn't for the life of me wrap my head around why people paid so much for them. they were paying for a piece of json data on a blockchain that referenced an image off-chain that could go offline at any time. and not only that, anybody could snag the jpeg you bought.

so my cousin and i decided to make our app different, starting with ownership. blockchain really limits how big of a file you can store on chain; crypto punks (i think) was able to do this though because they had small, pixelated images. but, my cousin knew that digital artists' original files were >= ~100MB so they could be printed very large if needed. so here was our pitch and what we though differentiated us:

- artists would upload their high-res images and *these* would be the protected assets. our website would load very low-res versions of the images
- collectors would basically buy an nft which allowed them to view and display the high-res image on their desktop as a background, their phone, or their tv. but they still technically didn't "own" the original file; i.e. they could not (yet) request a print of it, or get access to the raw file
- we learned how much of a pain it was to buy any kind of crypto (ethereum, bitcoin, etc). so we were the first marketplace to let buyers pay with a credit card through stripe. it was early enough that stripe and credit card companies didn't have a strong stance, so we were able to slip through the cracks. also, we didn't have any kind of crazy high volume so it likely wouldn't have been flagged
- collectors, after buying an nft, could then go into their dashboard and create custom playlists of their artwork, download our android tv app, and then view their high-res images on there. the goal was to also provide some way to let them show the image on their desktop, mobile device, and other places. but we didn't get that far, and that would essentially break our "security" model to protect access to the raw, higher res images
- this was also around the time when gas fees on ethereum were getting out of control. and to mint an nft would cost an artist like $10-$50 per nft! so i came up with a custom erc-1155 smart contract that would basically "lazy mint" the nft, and the buyer would pay the minting gas fee - not the artist. explained more later.

while this was technically fun an interesting to work on given the constraints, it was not a great business move.
- buyers were crypto bros who were flush with crypto at the time. they already had it, or were comfortable buying more. they wanted to spend their crypto; not pay with a card. we were early on the credit card thing (said another way: we were *wrong*)
- buyers didn't care about the high resolution artwork, or displaying it on their tv. they just wanted to buy the nft for reputation points, fun, or to then trade and try to make a quick buck (i.e. gamble)
- most artists didn't actually care about people being able to download a screenshot of their artwork. they would only release a 1024x1024 or 2048x2048 max sized image anyways, and the good artists were getting paid so much money they didn't care about "protecting" their artwork (this was before diffusion ai models were big though!)

cool technical things i built to enable all of this:
- the custom erc-1155 smart contract. this lets you batch transactions as opposed to erc-721 which could only process one transaction at a time. to enable lazy minting, an artist could specify ahead of time how many pieces of a certain type of artwork could be minted. this was just one, small transaction. after that, a buyer could buy a new nft, the new nft would be minted with the artist listed as the creator in the contract for provenance, and the new owner would be the buyer.
- custom payments integration with stripe that would give the user a timed checkout with a window where the amount they paid in usd would be converted from eth based on the current price, plus some extra percentage to ensure the transaction was processed quickly, and if we ended using less than what they paid, they would be refunded the difference.
- a custom nft auction contract. fortunately, several major nft auctions had gone awry and the security community wrote out detailed blog posts on how to create the safest possible auction contract. i ended up creating a really subtle bug in our auction contract, which was supposed to run for 24 hours, but would only run for just over 18 hours. i don't remember the exact details, but i did a lazy comparison to determine if it was time to end the contract, and since i didn't use an explicit variable in the comparison, the ints were being cast down to 2 bytes, so an auction could at most run for 0xffff / 65,535 seconds which translates to ~18.20 hours.
- since we wanted to protect the high res images, and we wanted buyers to be able to view the images on their tv (via an android tv app), i needed to solve a few different problems:
    - first, the original sized files are all pretty large; most of them over 100MB. the hardware on android tvs was **not** meant to store much data. i think most only had like 8GB of onboard storage. and obviously very little RAM. so, we can't store these massive images on there, and likely can't cache many images, so we would also need to be downloading massive images every time which would take a while. so i ended up creating a lambda process on image upload that would quickly create multiple, resized smaller versions of the image: one for the website at 768x768 max, 1024x1024, and 2048x2048 max (it would maintain aspect ratio). then we could store multiple images and/or cache them.
    - second, it was highly unlikely, but someone could feasibly grab the images off the device if we stored them without encryption. so i created a simple drm-like feature that would encrypt each image with a unique key the first it was pulled, and it would only decrypt in memory. when the app wasn't in use, the downloaded images were stored encrypted in whatever secure enclave type feature the android hardware had. in order to decrypt the image, the app would need to request the key from the server, which would also help prevent unauthorized use if the collector sold that nft and should no longer have access to it. if we determined they sold it, we would delete it from their device.
    - third, eventually we wanted to support gifs or video files. for this, i actually needed to integrate with a drm platform to make this all work. it was not terribly difficult, but i remember not liking the experience at all.

this was honestly a really great experience, and this was all done over the course of ~one year. but neither myself nor my cousing realized just how difficult it would be to build a two-sided marketplace. he had half of the marketplace solved (artists), but we had trouble finding buyers when platforms like Foundation, OpenSea, Makersplace, Nifty Gateway, and so on were crushing it.

the biggest lesson? we could have made more money together if we worked to get him on as many platforms as possible to sell his artwork and maximize how much money he could have gotten. and perhaps even consulted with other artists to help them do the same and perhaps take a small cut.

i found our old [kickstarter video](https://www.crowdfundingpr.org/tabu-art-launches-on-kickstarter/) which is kind of funny to watch. you can tell we both have a lot of experience speaking in front of a camera 😂 despite how serious it looks, we actually laughed a lot at ourselves that day trying to get better and better takes.


### game building experience

these were all relatively simple games, but still a great learning experience. at some point i think would be very interesting to build my own physics and game engine just to learn. but now is not that time.

#### a couple of web-based hytopia games

i built two games using hytopia's sdk. these were both for game building competitions, but also made for fun side projects.

the first one was called The Overseer. it's a single or multi-player co-op game where you're stuck in a damaged biodome with a rogue ai operator in charge of protecting the biodome. it sees you and other players as hostiles and tries to eliminate you using its biodome control system. attacks included things like increasing and decreasing temperatures to hurt you, a uv light that targets one player and follows them around (if you get stuck or stop moving, it can do some real damage), ground electrification, and so on.

i designed it such that the game would collect global game state including players remaining, player health, current biodome temperature, and so on, feed it to an llm, and have the llm use structured output to determine what actions to take next, and what taunts (if any) to communicate to the players. i used a tts model hosted on replicate.com to convert the text the speech, and then had a script that would apply randomized distortions to the voice depending on the ai overseer's remaining health. lower health meant a higher chance of significant corruption to the audio file; higher health meant mostly stable audio file. the inspiration for all of this was glados from the portal games, as she becomes increasingly paranoid and glitchy.

the tts feature was a little tricky to get working. hytopia game models, audio, etc are all contained in your game folder in a directory named `assets`. so i had python api service running on the same machine as my hytopia game code, and the api service was the one responsible for making the api calls to the llm and replicate.com for tts. it would then get back the tts file, run the corruption script, take the output audio file, and shove it into the assets folder where it needed to be, along with a unique file name. after the audio file played, it was deleted to avoid cluttering up the folder.

[overseer game demo](https://x.com/gabebusto/status/1912167058596372716)

i also created a fun little first person shooter game called battle cube. it was a simple deathmatch style game fought on what looks like a giant rubiks cube with weird structures on the surface for more interesting gameplay.

there wasn't much special about this, but there were some fun details.

i added a rubber chicken gun (did NOT fit the blocky aestheic; remember, this is why i created blocksmith in the first place!) that would launch little chicken grenades at people. there was also no special effects at the time in the sdk so i had to get creative in making what looks like an explosion. which was basically by creating a 3d model of some kind of comic explosion look, and creating several at the ~same time at increasing sizes and having them quickly fade in and out. it also made a rubber chicken noise 😂

[chicken gun demo](https://x.com/gabebusto/status/1907252002712682868)

i also added a fun item to the game: the birthday cake 🎂 whoever consumed this item was safe. but the game would then pick the current player with the best kill-to-death ratio, dim all the lights, shine a bright spot light on them that follows them around, and plays an obnoxious happy birthday song on repeat until they are killed.

[birthday cake demo](https://x.com/gabebusto/status/1903892581869617594)

and here's a look at the final map and game:

[battle cube demo](https://x.com/gabebusto/status/1907040018863992878)


## previous work experience

### since august 2023
i wanted to focus on learning about ai and how to make money outside of traditional employment (including consulting / freelancing).

this was when developed all of the ai apps i shared above (and more that i didn't share that were earlier prototypes and apps that were more like simple wrappers).


### eyris - senior software engineer (contractor) - march 2023 to august 2023
eyris is a company that was exploring ways to use private blockchain networks for enterprise security level applications for the government.

the role involved standing up a stable [Besu private IBFT network](https://besu.hyperledger.org/private-networks) of nodes, and building different applications on them to demo different capabilities that may have been interesting to potential customers.

i worked on making the network deployment from scratch much faster by automating it using terraform.

i also explored some interesting research-based projects for potential demo applications such as using zero knowledge proofs for communication between medical facilities and insurance companies without compromising user privacy.

i opted not to renew the contract to pursue some of my own ideas.


### stripe - solutions architect - september 2021 to november 2022
this was an awesome job. i landed it in part due to my entrepreneurial journey of building tabu art (the nft art marketplace) and my experience integrating stripe with it beyond just a simple checkout page example.

but this was entirely new territory for me because i had always worked as engineer. so i had a learning curve, but it didn't feel that rough. i joined pre-sales calls as a technical expert, along with an account executive, to help learn about what problems our potential customers had. i had to map that back to our product suite and think about things like what product would work for them, what would their specific api setup look like, what kinds of legal issues would we need to get clarification on, and so on.

the goal was to make sure that i helped align the customer at this early stage with exactly what they needed to do in order to integrate stripe and solve their most pressing payments problems. if i did my job right (along with the rest of the deal team), they could go on to execute the integration plan i gave them and go live as quickly as possible.

the role involved keeping up with and more deeply learning stripe's api (which is a lot of ground to cover!), learn how to ask the right questions to discover real pain points, figure out where to go get any number of questions answered (legal questions, deep product questions, roadmap questions, architectural questions regarding proposed solutions, and so on), help push the deal cycle along and reveal our proposed solution, clarifying that we're all on the same page about the solution, then creating a nice integration plan for the customer's technical team to implement.

it was one of the most interesting roles i had, but i ultimately realized it was too far away from the technical work i wanted to do. i enjoyed finding new corners of the stripe api and learning how it worked and when they would be useful, learning about edge cases, building demos for customers, etc.

towards the end of my time there, i - with my manager's blessing - started asking some technical teams if they would take me on as an engineer. i had a lot of great conversations and found at least two teams i could switch to, but the entire company had a freeze on hiring and transfers. it turns out this was due to them preparing for their big 2022 layoff of 11%, by which i was affected along with 90% of my team.


### tabu art - cofounder - may 2020 to may 2021
this is the nft art marketplace i worked on and described in more detail above.


### raytheon - senior cyber engineer ii - june 2013 to june 2020
this was an incredibly awesome job to get out of college. i didn't start learning to code until maybe 2011 or so (my ~sophomore / junior year) which could be said to be pretty late in life. i forced myself to use linux once i got into coding, and eventually found myself enamored with computer security. one Christmas i got the book Hacking: The Art of Explotation, and i was hooked.

i spent my last 6 months in college devouring the corelan exploit series blog tutorial and learning how vulnerability research and exploitation worked, and was able to land an internship with a small team at raytheon focused on computer security research.

i started out with a simple task of looking for vulernabilities in a simple internal java web application. it was gruntwork nobody wanted to do and was considered boring. i remember that was the about the time i learned how to use grep, and i blew that application wide open.

from there i continued to pick up tasks that nobody wanted to do and kept quickly learning. i even helped create some contrived security training exercises, writing all kinds of random python security scripts, and whatever else i could get my hands on. i became more comfortable using tools like ida disassembler to read and understand what was happening for architectures like x86/64 and different mips variants. i even got to write some kernel-level code which was a pretty valuable learning experience.

i eventually "graduated" and got the chance to work on one of the hottest teams where i could actually do more open ended research on harder stuff, and occasionally build proof of concepts for cves. i managed in a few cases to find critical issues like hidden backdoors in some expensive networking equipment, and even created a full end-to-end exploit of a bug i found, with a multi-stage payload to end up controlling the device.

around mid-2017, most of my good friends had moved up to the office near washington dc, and i decided to transfer up there along with them. and this is when my career there took a turn from being focused on security research to more of a developer role. for ~1-2 years i worked across a few teams on established products where they needed a developer and to work on embedded realtime systems, to mobile devices, to higher level applications like browser clever browser fingerprinting solutions.

i eventually got the chance to lead the (i think objectively) highest impact project there. and it was a humbling experience. the team had been working on this product for years, and they were all incredibly talented. my job was to try and rescue the project because the previous tech lead had literally been defrauding the company and not doing their job. the engineers were left to deal with the mess and couldn't focus on the product, and the most experienced engineer was on the verge of quitting. so my job was to come in, get the project back on the rails, and remove any and all obstacles so they could continue delivering, and our key engineer could happily do the work we needed him to do.

it was tough taking a step back from doing technical work, but highly rewarding to help turn things around and let them focus on what they did best and stay on track. we hit every release after that and were able to keep a strong relationship with our customer and retain our key engineer for the project.

in the months leading up my departure from raytheon, i knew i was getting close to wanting a change. so i was able to find someone to shadow me for a few months to get a feel for the role. in the end, i was able to hand it off smoothly to ensure they didn't have another crisis.