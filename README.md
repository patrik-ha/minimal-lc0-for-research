# A lc0-package for research

## What is this?
The main intention of this repository is to provide a sort of "starter pack" for the curious researcher who wants to take a look at chess-playing neural networks. This is done by providing ready-to-go model files for one iteration of the model(s) from the (Leela Zero Chess project)[https://github.com/LeelaChessZero/lc0]. The repository aims to make it as easy as possible for researchers familiar with standard ML tools to start tinkering with large, pre-trained chess models.

## Why?
There is inevitably a lot of fancy engineering work required for making something as well-performing as lc0. While this is necessary for a project with the primary goal of optimising for the playing strength of their model, this can make the barrier to entry for many machine learning researchers quite high. Most ML researchers might not be well-versed in C++ for example, but would most likely still be very interested in using these chess models in their research if some of the more heavy techinical lifting was done for them. In the age of datasets and models with dubious ethical standards (and notoriously closed source initiatives like AlphaZero), it would be a shame if researchers passed up the opportunity to work with cases like this, where really strong (and interesting!) models and projects are open source and generally available for everyone.

## What _exactly_ does this repository provide?
This repository mainly provides two things. It provides model snapshots for Pytorch (WIP) and TensorFlow of a *single*, strong (somewhat outdated) model trained by the lc0-community. It also provides simple ways of creating input-data based on either FEN strings or PGNs, where the main mantra is to make it as close to handling any other neural network task in your favorite machine learning framework. And that's it!

## What does this repository *not* provide?
For optimal playing strength, lc0-models use Monte Carlo Tree Search to search for what it considers to be the best move. This is not included in this repository. If you want to use these models for *playing* chess, the lc0-community has a lot of really great tools you can use. Additionally, if you know that you are mostly going to be interested in looking at the direct outputs of the model, the lc0-repo also includes some handy Python bindings you can use for that, and tools for converting *any* of their models to the standardized ONNX format.

The repository also (probably) won't have the all of latest and greatest networks from lc0. (In fact, the repository only has a single one. The plan was to have a more complicated setup for downloading and converting arbitrary models, but until now the simplest case still remains. If you want a research-example of getting and adapting more models than just one, you can check out the instructions for (https://github.com/patrik-ha/ii-map)[https://github.com/patrik-ha/ii-map]).

Thus far, the project only ships with one of the later training iterations of the T30-range of lc0-networks. This is the same architecture as AlphaZero. (This particular architecture was chosen as it is probably familiar to most people interested in this field, and with an architecture that is not excessively complicated. It also makes for an easy citation I guess.)

## Enough talk, how do I get started?
The project includes the same neural network in both Pytorch- and TensorFlow-formats. These networks are then ready to be used as any Pytorch- or TensorFlow-model! These are located in `models`. (TensorFlow-version currently available, Pytorch is a WIP) 
### The models are zipped! Unzip them into the same directory and keep going.

This project also includes functions for converting FEN-states (directly or from PGNs) into input-states that you can give to the model for inference. (Adapted from https://github.com/so-much-meta/lczero_tools. Thanks!) 

The input format of the networks included in this repo is described briefly in the following figure.
*TODO*

The main thing to note is that the `LeelaBoard` class uses (almost) the same API as `python-chess`. You push moves to it (that you make yourself, or that you read from a PGN), and then its nice functions let you extract an input sample for each state you are looking at. Note that since the network actually uses the last 8 states as input (and not just the current one), you might get different results for the same position depending on the ones leading up to its.

You can find some examples for how this all works in [examples](/examples).

Some of these examples are adapted from some of my own research works. I (the project author) am in general very interested in chess-playing neural network models, and have worked a bit with applying Explaimable AI techniques to chess as a domain. (and I talked to a bunch of people who would like to do the same, but were a bit scared by the (reasonable) barrier to entry of interfacing with these models)

## Acknowledgements
The code for converting FEN-states to input-samples uses snippets from (https://github.com/so-much-meta/lczero_tools)[https://github.com/so-much-meta/lczero_tools]. Thanks!!
