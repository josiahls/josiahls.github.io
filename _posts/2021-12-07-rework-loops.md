## Why try to re-work Fastai Version 2 Loopiing?

TBH 60% if this is readability/visability.
- what fields does a callback read?
- what fields does the callback modify?
- why are metrics treated differently? They seem like just custom callbacks? Transforms seem similar, except they occur at the data loading part of the training loop and can run on GPU/separate process
What if I dont want to do validation during a fit (RL?)
How do you add a test set?
How long does each part of the loop take to execute?
- fastaiv2 (Learner) has a traditional training loop that generally has 1 model, 1 opt, 1 loss. You can argue you can have multi- behavior, but in general, that is the training loop, and trying to augment that is kind of weird. For example DDPG/SAC have 2 opts, can have separate losses (from what I remember).  Even worse, one part of the model might need to be trained/optimized before the other (any AC model I think)
- fastaiv2 DataLoader: Pretty confusing and doesnt support callbacks the way the Learner does, but seems like they both are trying to accomblish the same thing, just that the fastaiv2 DataLoader's callbacks are called "transforms"... transforms and callbacks seem to have a generally similar idea behind them. 
   - The fastai dataloader is not as flexible as they say, and is really confusing to read. I think re-writing this with a generic loop API+the new TorchData would make it way better.

There are 2 other loops I found for RL: agent execution, and iterating through a gym env. Maybe Learner/Agent/Gym can have generic loop tooling?

Initially I have https://github.com/josiahls/fastrl/blob/main/nbs/03_callback.core.ipynb but now im trying out https://github.com/josiahls/fastrl/blob/main/nbs/02_fastai.loop.ipynb , I don't have a working new version of a loop yet though, but roughing out some ideas. There are some frameworks that are trying something similar, but im curious if I can do something better (but also eventually help with fastaiv3)
