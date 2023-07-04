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

LHC is building a tremendous physics legacy through the vastly many analyses performed by the experiments. CMS alone has published [more than a thousand physics analyses]([https://arxiv.org/abs/2205.09597](https://cms-results-search.web.cern.ch/)https://cms-results-search.web.cern.ch/). These analyses focus on a large spectrum of physics goals ranging from standard model measurements to searches for new physics. Each of these analyses investigate well-defined final states that  characterize predicted signatures from a physics model or a set of physics models.  The physicists who originally design and perform an analysis usually interpret the analysis result based on one or more physics models.  

> ## Experimental result vs. interpretation
>
> **Results** and **interpretation** are two terms that are sometimes used interchangeably, even though they refer to two very distinct concepts. Let us first clarify those:
>
> * An **experimental result** is the empirical outcome of the experiment, the measurement of some physical quantity, such as counts, cross sections, signal strengths, masses, etc.
> * **Interpretation** is the comparison of experimental results with the expectations of a given a theoretical model.  
>
> {: .source}
{: .callout}

However time and resources are limited, and the priority in an analysis is to produce the result. Therefore, the analysis team only interprets using a limited number of models, or limited subsets of parameter spaces to demonstrate the analysis' usefulness. Yet, the analysis may be sensitive to many other theoretical models not addressed by the original study.  Moreoever, it would be a waste to not interpret an analysis produced in many years by such great effort, on as many models as possible.  The effort of reusing information from an analysis to interpret it in terms of theoretical models not addressed by the original analysis, is called **reinterpretation**. 


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

