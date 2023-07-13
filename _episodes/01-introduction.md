---
title: "What is reinterpretation and what is the role of open data?"
teaching: 20
exercises: 0
questions:
- "What is reinterpretation?"
- "What are exact and optimized reinterpretation?"
- "What inputs are needed to perform reinterpretation?"
- "What is the role of open data in reinterpretation?"
objectives:
- "Learn the concepts of exact reinterpretation and optimized reinterpretation."
- "Learn the inputs needed to perform different types of reinterpretation."
- "Learn the role of open data in different types of reinterpretation."
keypoints:
- "Reinterpretation is the comparison of experimental results with the expectations of a given a theoretical model which was not already interpreted by the original analysis publication."
- "Reinterpretation requires running, and usually even rewriting the analysis. One can use the original analysis as it is (exact reinterpretation) or a modified version of it to optimize signal sensitivity (optimized reinterpretation.)"
- "Open data is a great source of events, in particular for optimized reinterpretation studies."
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

There exists a dedicated [LHC Reinterpretation Forum](https://twiki.cern.ch/twiki/bin/view/LHCPhysics/InterpretingLHCresults) aiming to provide a platform for continued discussion of topics related to the BSM (re)interpretation of LHC data, including the development of the necessary public and related infrastructures.

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

Exact reinterpretation studies do not need to rerun the analysis over data or backgrounds, but only run on signals.  Therefore usually a simplified public fast simulation package, such as [Delphes](https://cp3.irmp.ucl.ac.be/projects/delphes) is used for simulating the detector performance.  Consequently, analyses are also written in a more simplified manner, e.g. with simpler object definitions. MA, CM.

There is also the [RECAST framework](https://iris-hep.org/projects/recast.html) that runs the original analysis chain given signal events at LHE format.

This is the most commonly used reinterpretation method up to now.  But perhaps it is time we get more creative! 

### Optimized reinterpretation

What if you have a physics model whose final state is not explored by the existing analyses? 

You may of course design a brand new analysis directly targeting your signal, run it over data and full background and signal MC. But developing a complete analysis from scratch with a sound methodology is time consuming and far from straightforward.  Another less daunting option could be to take an analysis that explores a final state as close as possible to your signal prediction, and slightly modify its selection criteria to get optimal sensitivity for your model.
This option still requires processing the full set of data, background and signal samples. Yet it provides a more secure approach, as one can compare the consistency of event yield predictions between the original and the modified analyses to avoid errors.

For optimized reinterpretation studies, we need:
* **The full set of collision data:** Provided as open data.
* **Background and signal samples:** MC for most SM processes and some BSM processes are available as open data samples. Other signal processes can be produced as in the case for exact reinterpretation.
* **Analysis code:** We need analysis code that can process real collision data and MC samples.

> ### What can we modify in an analysis?
>
> What kinds of small modifications can we make in an analysis to optimize its sensitivity to a different signal model? 
>
> ### Solution
> 
> * Modify / add some cuts in the event selection.
> * If there is a machine learning model for signal discrimination / extraction, retrain it for our signal model.
> * Change binning of the analysis variable.
> * Mofify object selections, e.g. raise pT, use tighter isolation, ...
> * ...
>
{: .discussion}

## Open data for reinterpretation

How can we use open data for reinterpretation? 

### Open data for exact reinterpretation

Let's remember that exact reinterpretation only requires signal events.  Open data consists (will consist) of plenty of SM and BSM MC samples with CMS detector simulation.  There is a chance that our signal of interest is already available in open data.

> ### Where is the actual need for open data in exact reinterpretation?
>
> We may ask the following question, especially for BSM signals: If CMS has produced the signal events, were not they already used in a dedicated analysis? What situations may trigger the reuse of these events in the exact reinterpretation context?
> 
> ### Solution
> 
> * Different analyses are developed under different working groups.  Multiple analyses can end up addressing similar final states.  We may want to compare sensitivity for a signal in different analyses.
> * Study of excesses: Various analyses observe excesses over the SM. As new excesses are seen, we may want to compare and combine with older analyses for a variety of signals.    
> 
{: .discussion}

### Open data for modified reinterpretation

Here, we absolutely need open data, as we must reprocess collision data events with the optimized analysis in order to obtain the analysis result. Open data is the only source of collision data.  The large numbers of officially produced SM and BSM Monte Carlo events, simulated consistently with data would also be directly available for use.  

{% include links.md %}

