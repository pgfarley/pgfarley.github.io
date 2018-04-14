On April 5th the folks at OpenAI launched a reinforcement learning contest[LINK] based on the first three Sonic (https://en.wikipedia.org/wiki/Sonic_the_Hedgehog#/media/File:SonicTheHedgehog1.png)
games for Sega’s 16-bit Mega Drive game console (aka the Sega Genesis in North America).
(https://en.wikipedia.org/wiki/Sega_Genesis#/media/File:Sega-Genesis-Mod1-Bare.jpg)
The goal of the competition is to create an AI player agent that advances the furthest through a set of custom and undisclosed game levels. 

The official website [LINK] includes a Quickstart for getting up and running. Following those instructions is a highly recommended first step for anyone looking to get involved in the contest. As a follow on I thought I’d write-up a brief guide to the assorted tools and libraries that get used in the Quickstart. Hopefully learning a bit about the various pieces of contest infrastructure and how they hang together will be useful background for this contest as well as for future projects based on OpenAI’s infrastructure.

OpenAI Gym

The Gym toolkit is the core project that all other contest tools build on. The official site [LINK] describes it as “a toolkit for developing and comparing reinforcement learning algorithms”. In practice, understanding what Gym is for requires understanding a little bit about a standard reinforcement learning metaphor.

In reinforcement learning, the machine learning “problem” is structured as Agents making Observations of, taking Actions on, and collecting Rewards from an Environment. The passage of time is broken up into discrete Steps.

 [IMAGE]

The Gym toolkit provides a handy Python API for working with this characteristic reinforcement learning structure. Concretely, in the OpenAI contest, the Environment is the Sonic game, the Agent is the player algorithm implemented by contestants, the Observations are game state data at a given time (screen pixels, remaining lives, etc), the Actions are console controller commands (up, jump, left, etc), and the Reward is the percentage of level completed.

 [IMAGE]


Let’s take a look at the random agent

Render (SimpleImageViewer)

Gym is useful for all sorts of stuff

MUJUCO Agent
[VIDEO]
Code
Beauty of Gym, one interface 


Sutton book 1.1 and 3.1

https://gym.openai.com/docs/

Environments

