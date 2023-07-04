---
title: "What is reinterpretation?"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## What is reinterpretation?

LHC is building a tremendous physics legacy through the vastly many analyses performed by the experiments. CMS alone has published [more than a thousand physics analyses](https://cms-results-search.web.cern.ch/). These analyses focus on a large spectrum of physics goals ranging from standard model measurements to searches for new physics. Each of these analyses investigate well-defined final states that  characterize predicted signatures from a physics model or a set of physics models.  The physicists who originally design and perform an analysis usually interpret the analysis result based on one or more physics models.  

> ## Experimental result vs. interpretation
>
> **Results** and **interpretation** are two terms that are sometimes used interchangeably, even though they refer to two very distinct concepts. Let us first clarify those:
>
> * An **experimental result** is the empirical outcome of the experiment, the measurement of some physical quantity, such as counts, cross sections, signal strengths, masses, etc.
> * **Interpretation** is the comparison of experimental results with the expectations of a given a theoretical model.  We use a **statistical model** that relates to observed quantities in data (e.g.. counts) to the theoretical model parameters (e.g. BSM particle masses, cross sectons). Take the simplest case of a counting experiment with observes data counts **D** and estimated background **B** after the analysis selection:  interpretation first calculates the signal counts **S** predicted by the model after the analysis selection, then checks whether observed data **D** are more consistent with the background hypothesis **B** or the signal plus background hypothesis **S + B**.  From here, we can assess if the analysis has discovered or excluded the signal, or if it is not sensitive enough to observe the signal.   
>
> {: .source}
{: .callout}

However time and resources are limited, and the priority in an analysis is to produce the result. Therefore, the analysis team only interprets using a limited number of models, or limited subsets of parameter spaces to demonstrate the analysis' usefulness. Yet, the analysis may be sensitive to many other theoretical models not addressed by the original study.  Moreoever, it would be a waste to not interpret an analysis produced in many years by such great effort, across as many models as possible.  Reusing information from an analysis to interpret it in terms of physics models not addressed by the original analysis, is called **reinterpretation**. Reinterpretation is typically done by phenomenologists to see the impact of experimental results on their favorite physics model.


## Types of reinterpretation

We can reinterpret an analysis in different ways. We can either reinterpret an analysis as it is, or we can modify the analysis selection.
But whichever way we choose, reinterpretation requires rerunning the analysis code on events, and most of the times, recoding the analysis from scratch to some extent of accuracy! 

### Exact reinterpretation

We employ exact reinterpretation when final state explored by the analysis matches that predicted by our physics model of interest (**perhaps give an example**).
Exact reinterpretation uses the analysis as it is.  This means, the analysis selection and all other details stay the same as in the original study.  Consequently, the analysis results (e.g. data counts, background estimations, uncertainties) can be directly taken from the experimental publication.

The missing piece is the signal prediction, and here is how we can do it:
1. **Obtain Monte Carlo (MC) samples for the signal model**: Generate events and preferably apply some sort of detector simulation. 
2. **Obtain a valid analysis code**: Sometimes analysis code that can run on the format of events you have, can be publicly available. If not, you would have to re-write and validate it yourself. Write at least the signal selection as consistently with the original analysis as possible.
3. (If you had to write the code) **Validate the analysis code:** Make sure that the code is correct by running it over signals used by the original analysis and comparing your signal predictions, e.g. counts, cutflows, with those provided by the analysis team.  This is the most tricky part!
4. **Run the code on signal events:** Run the code to obtain predictions for input to the statistical model.

Exact reinterpretation studies do not need to rerun the analysis over data or backgrounds, but only run on signals.  Therefore usually a simplified public fast simulation package, such as [Delphes](https://cp3.irmp.ucl.ac.be/projects/delphes) is used for simulating the detector performance.  Consequently, analyses are also written in a more simplified manner, e.g. with simpler object definitions. 

This is the most commonly used reinterpretation method up to now.  But perhaps it is time we get more creative! 

### Modified reinterpretation

What if you have a physics model whose final state is not explored by the existing analyses? 

You may of course design a brand new analysis directly targeting your signal, run it over data and full background and signal MC. But developing a complete analysis from scratch with a sound methodology is time consuming and far from straightforward.  Another option could be to take an analysis that explores a final state as close as possible to your signal prediction, and 

Reinterpretation usually consists of 

**Reinterpretation** consists of recoding a published analysis from scratch for the purpose of interpreting it in terms of other physics models not interpreted in the original publication.
Reinterpretation is usually done by phenomenologists to see the impact of experimental results on their favorite physics model.
* An analysis code is rewritten outside the experimental frameworks.
* Analysis recoding is done less accurately compared to the original experimental code, since detector information does not exist in full detail in public simulation tools.
* Public tools exist for rewriting analyses: CheckMate, MadAnalysis, Rivet, … now ADL/CutLang.
* Monte Carlo simulated events for the signal models are produced.
* Analysis code is run on the events to obtain predicted signal counts / efficiencies.
* Predicted signal counts are used together with observed data and background estimation results
from the experimental publication to calculate limits.

{% include links.md %}

