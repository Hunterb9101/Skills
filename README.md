# HunterB9101 / Skills

## Background
Over the past few months, I've been working on integrating AI into my development workflow, trying various concepts such as a Research/Plan/Implement workflow, 100% vibe-coded approaches, or as a HITL process.

While I have seen some success in the area, there have been a number of roadblocks that have limited my use of the tool:

1. **No Improvement Loop**: I find that after writing a prompt, I rarely end up improving on it. This leads me to be recreating my prompts from the ground up, and running into a new set of issues every time I run something. This is an inefficient use of my time.
2. **Unclear Skill Ownership**: I have waffled on whether I should be packaging codex skills with my github repositories. This has led to inconsistencies with how skills are tracked/versioned, and that also means I'm having to copy skills between repositories. I forget about skills I've created, and then up writing them from scratch (The number of Python code skills I've written is much higher than I'd like to admit). This again, leads to an inconsistent AI experience.

In order to solve both problems, I've created a small repository to house my personal AI skills. This will help enable consistency across the different places that I use the skills, and hopefully lead to the development of a tighter improvement loop of agentic processes.

## Skills

### Contribute-Python

_Writes Python in a way that mirrors how I write it._

When I've used codex in the past to implement a feature, there have been a couple of friction points:
1. Nearly every project I work on needs a specialized virtual environment to run properly. Codex consistently attempts to run python with the default interpreter, and then does one of two things. It either burns a ton of tokens to figure out there is a venv it can use and activates it, or it attempts to install a bunch of packages globally. Both of which burn a ton of tokens.
2. Out of the box, I expect a certain level of separation of concerns. I don't want configuration values driving behavior deep in library, I/O where it isn't necessary, nor extensive validation at every step. It makes it hard to test behaviors, and harder to follow. However, I commonly forget to mention this when prompting, and I end up with a feature that decreases the readability of the codebase with a bunch of odd behaviors.
3. Codex _loves_ writing a bunch of code for reverse compatibility, and most of the time I am writing experimental Data Science code. This leads to a disconnect where I expect some functionality to be adjusted/removed, but we end up adding a bunch of bloat to support both paths, hindering readability.

### Publish-Issue

_Publish an issue to a Github Repository._

I commonly develop across multiple repositories, usually with one functioning as a generic library, such as [`ml-tools`](https://github.com/Hunterb9101/ml-tools) and another as my experiment environment, such as [`kaggle-competitions`](https://github.com/Hunterb9101/kaggle-competitions). I have had a habit of developing both the library _and_ the experiment in parallel, to the point where I have both open at the same time. While this has worked for me in the past, I recognize that it leads to a rapidly-changing generic library, and then I'm stuck attempting to both solve something in the specific _and_ generic case. I'd like to slow down the velocity of changes to `ml-tools` and other library repos to be more intentional what ends up in it. To do this, I'll use GitHub Issues to track my proposed changes - effectively pushing off trying to solve the generic case to a later date.

However, I also recognize that writing a good issue ticket requires a great deal of consistency and effort. This skill helps take an unstructured view of bugs and potential features, and organizes them into a consistent format that can be used later by either me or a coding agent to understand and solve a problem.

## Resources
- [What is a skill?](https://openai.com/academy/skills/)