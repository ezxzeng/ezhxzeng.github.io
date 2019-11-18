---
layout: post
title: post hackathon
date: 2019-11-17
---

The two most important things to fix:
1. The training pipeline was messed up somewhere and was unable to show validation loss properly 
2. the dataset was small and only contained british english

## Training pipeline
Since I'm no longer constrained by the time limit of a hackathon, may as well just rewrite the whole thing without bothering with tensorflow's thing.

I'll still train first on tensorflow's [speech command dataset](https://ai.googleblog.com/2017/08/launching-speech-commands-dataset.html) first before training on "um"s. This time, I'll try to find a way to train the base model on the full dataset instead of just a single word. Meaning when transferring, replace the output layer shape.

## Dataset
in addition to from before, new datasets:
- CallHome English corpus of telephone speech (https://ca.talkbank.org/access/CallHome/eng.html)
- Santa Barbara Corpus of Spoken American English (https://www.linguistics.ucsb.edu/research/santa-barbara-corpus)
- The Buckeye Speech Corpus (https://buckeyecorpus.osu.edu/) if the above isn't enough
- LDC Spoken Language Sampler (https://catalog.ldc.upenn.edu/LDC2017S16)