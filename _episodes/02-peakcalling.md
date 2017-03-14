---
title: "Peak calling with MACS2"
teaching: 15
exercises: 30
questions:
- "How do we go from aligned reads to transcription factor binding sites across the genome?"
objectives:
- "Be familiar with peak calling using the MACS2 software packages."
- "Be aware of the different arguments, and their default values, in MACS2 when peak calling." 
keypoints:
- "MACS2 is an easy to use peak caller with a range of different options that can be provided." 
---
# Overview of peak calling in MACS2

# Installing MACS2
Installation of MACS2 requires that you have Python installed on your system. This is not usually an issue for any Linux and Mac machine, since these systems usually ship with Python already installed. Also, you will need *Numpy* and a *GCC* compiler installed. *Numpy* can be installed using the *pip* package manager of Python, while *GCC* comes installed with all Linux distributions (for Mac users, you will need to install X-Code). Once you have these packages installed, installing MACS2 is simply done using the following:

~~~
pip install MACS2
~~~
{: .bash}

One way to check if MACS2 is properly installed is to issue the command `macs2` at the terminal. You should see the following, which will indicate that MACS2 has been installed: 

~~~
usage: macs2 [-h] [--version]                                                                                                                                                                    {callpeak,bdgpeakcall,bdgbroadcall,bdgcmp,bdgopt,cmbreps,bdgdiff,filterdup,predictd,pileup,randsample,refinepeak}                                                                   ...                                                                                                                                                                    macs2: error: too few arguments 
~~~
{: .output}

# Predicting fragment size 
In ChIP-seq, the reads sequenced usually represents the ends of the DNA fragment and not the exact binding location. One common strategy that is used to recover the actual binding site is to extend the reads to include the actual binding site. However, one needs to determine how long should the reads be extended to. There are two ways of doing this, namely:

1.Make assumptions about the length. For instance, one commonly used value for transcription factor binding site is 200bp. 
2.Use the strand cross-correlation to estimate a fragment length. This can be done using `macs2 predictd`. 

# Peak calling with MACS2
Peak calling in MACS2 is done using `macs2 callpeak`. There are a large number of different options that we can provide. 
