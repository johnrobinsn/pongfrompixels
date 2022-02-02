# pongfrompixels
This repository contains updated code for Andrej Karpathy's article, "Deep Reinforcement Learning: Pong from Pixels" the code linked from that article is a bit dated having been written for Python 2.  This repo contains Andrej's code updated to support Python 3 and some support for tensorboard logging.  All credit goes to him for the code.

Here is the [companion blog article](https://www.storminthecastle.com/pong_from_pixels) for this repostory.

## Setup Environment
I recommend that you use a python version manager.  I use [conda](https://docs.conda.io/en/latest/).

Usong Python 3.7 and Conda

```
conda create -n pongfrompixels python=3.7
conda activate pongfrompixels
```

Use pip to install the required python modules

```
pip install numpy gym[atari] gym[accept-rom-license] pyglet
```

## Demo
I've provided a pretrained model contained in the file, 'best.p'.  You can run and render the pretrained model as follows:

```
python pg_pong.py --demo
```

## Train
To train the model from scratch just run with *no additional command line arguments*.  The model will be saved periodically to a file, 'save.p'.  If you need to stop training for any reason you can stop the program and use the resume option described below to pick up training from where you left off.

Note: *The file, 'save.p', will be overwritten periodically so if you get a really good model you might want to save this off.*

```
python pg_pong.py
```

If you'd like to see the pong game rendered in a window while you train use the render option.  This will slow down training a bit but is still fun to watch (at least for a bit).

```
python pg_pong.py --render
```

## Resume
You can pick up training from where you left off by using the resume option.  This will load the last checkpoint that is contained in the file, 'save.p', and train from that point.

```
python pg_pong.py --resume
```

## Optional Tensorboard Logging
You can also **optionally** install support for tensorboard logging although not required to run the code.

Install the tensorboard dependencies.  Note: torch is only used for tensorboard logging support in this context.

```
pip install torch tensorboard
```

Then while the model is being trained you can run tensorboard in parallel specifying the runs directory that will be created.

```
tensorboard --logdir=./runs
```

This will run tensorboard and print a loopback url that you can paste into your browser (on the same machine) that can be used to display the tensorboard dashboard.  The average reward is the only metric currently logged.

