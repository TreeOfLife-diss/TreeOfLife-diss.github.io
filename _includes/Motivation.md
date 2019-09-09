# Motivation

The continuous interaction with end-users through workshops, presentation seminars, mailists Q&A and others, led us to understand that software installation is a crucial bottle neck between users and the software package itself. 

When asking users to install a software package, which we aim to distribute over a large scientific community, there is a clear difference between those with programming skills, regardless of the skill level, and those without any of these skills. For the later group, simple steps such as installing [Anaconda](https://www.anaconda.com/) and configuring (conceptualizing and using) a [Python environment](https://conda.io/docs/user-guide/tasks/manage-environments.html) are definitively not straightforward and can create a great barrier between the user and the software and even drive the users completely away from actually using that software.

Therefore, when developing a software for a community of users that is not expected *(nor required)* to have any programming skills to actually use the software, it is necessary to keep, as much as possible, the installation process within the most *universal standards*, and these are, and have been for decades:

1. download
1. unpack
1. _single-click_ install
1. _single-click_ run

Maintaining these standards can be challenging if one considers the diversity of computer platforms available - each user has a different computer/OS/configuration.

## Library vs. Software Package

An important conceptualization behind the motivation for developing Tree-of-Life is that distributing a _Library_ for programming is different from distributing a _Software Package_ for practical usage; ToL focus on the latter. The confusion arrives, however, from the fact that many scientific software is developed and distributed nowadays as programming libraries (mostly in Python), as such, these are nicely distributed through [Pip](https://pypi.org/project/pip/) or [Anaconda](https://www.anaconda.com/distribution/) packages. But, distributing software packages through Pip or Conda might not be the best option *(or the only option to consider)* when these packages are not aimed to be used as libraries and target, instead, *non-developer* users.
