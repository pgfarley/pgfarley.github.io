## OpenAI retro contest

On April 5th the folks at OpenAI launched a [reinforcement learning contest](https://contest.openai.com/) based on the first three Sonic games for Sega’s 16-bit Mega Drive game console (aka the Sega Genesis in North America).
The goal of the competition is to create an AI player agent that advances the furthest through a set of custom and undisclosed game levels. 

The official website includes a [Quickstart](https://contest.openai.com/details) for getting up and running. Following those instructions is a highly recommended first step for anyone looking to get involved in the contest. As a follow on I thought I'd write-up a brief guide to the assorted tools and libraries that get used in the Quickstart. Hopefully learning a bit about the various pieces of contest infrastructure and how they hang together will be useful background for this contest as well as for future projects based on OpenAI’s infrastructure.

### OpenAI Gym

The Gym toolkit is the core project that all other contest tools build on. The [Gym site](https://gym.openai.com/) describes it as "a toolkit for developing and comparing reinforcement learning algorithms". In practice, grokking Gym requires understanding a little bit about a standard reinforcement learning metaphor.

In reinforcement learning, the machine learning "problem" is expressed as **agents** making **observations** of, taking **actions** on, and collecting **rewards** from an **environment**. The passage of time is broken up into discrete time **steps**.

 ![Reinforcement Learning](img/reinforcement_learning.jpeg)

The Gym toolkit defines a handy Python API for working with this characteristic reinforcement learning structure. Concretely, in the OpenAI contest, the **environment** is the Sonic game, the **agent** is the player algorithm implemented by contestants, the **observations** are game state data (screen pixels, remaining lives, etc) at a given time which is incremented in **step**s, the **actions** are console controller commands (up, jump, left, etc), and the **reward** is the percentage of level completed.

![Sonic as Reinforcement Learning](img/sonic_reinforcement_learning.jpeg)

The contest Quickstart includes an [agent](https://contest.openai.com/static/random-agent.py) that selects a random game controller action with each time step. In this simple example, the entire reinforcement learning problem structure is expressed in three lines of code!

Create an instance of the Sonic game **environment** and expose it as an object which subclasses Gym *[Env](https://github.com/openai/gym/blob/master/gym/core.py)*.
```python
   env = make(game='SonicTheHedgehog-Genesis', state='LabyrinthZone.Act1')
 ```

Advance time in **step**s with calls to *step()*. With each **step** the **environment** is passed an **action**, selected by a call to *env.action_space.sample()* which can be thought of as very simple **agent** algorithim that selects a random sample from the spaces of all **action**s defined for the **environemnt**.  After each **step** a float, *rew*, is returned indicating the **reward** for the current **step**. Similarly *step()* returns *obs*, a object with **observation** data for the Sonic game **environment** at this time **step**.
```python
    while True:
        obs, rew, done, info = env.step(env.action_space.sample())
```

Render (SimpleImageViewer)

Gym is useful for all sorts of stuff

[![Competitive Self-Play](https://img.youtube.com/vi/OBcjhp4KSgQ/0.jpg)](https://www.youtube.com/watch?v=OBcjhp4KSgQ)

Code


Sutton book 1.1 and 3.1

https://gym.openai.com/docs/

Environments. [LINK] create your own.

