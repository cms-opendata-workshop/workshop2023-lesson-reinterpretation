---
title: "Open data for reinterpretation"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Open data for reinterpretation

How can we use open data for reinterpretation? 

### Open data for exact reinterpretation

Let's remember that exact reinterpretation only requires signal events.  Open data consists (will consist) of plenty of SM and BSM MC samples with CMS detector simulation.  There is a chance that our signal of interest is already available in open data.

> ## Where is the need?
>
> We may ask the following question, especially for BSM signals: If CMS has produced the signal events, were not they already used in a dedicated analysis? What situations may trigger the reuse of these events in the exact reinterpretation context?
> 
> > ## Solution
> >
> > * Different analyses are developed under different working groups.  Multiple analyses can end up addressing similar final states.  We may want to compare sensitivity in these.
> > * Investigating excesses.
> > * ...
> >
> {: .solution}
{: .discussion}

### Open data for modified reinterpretation

...

## Reimplementing analyses for reinterpretation with open data


In most cases, we need to reimplement the analysis code for reintepretation. We may either start from 

* Use the code from the analysis team: Some analysis teams provide their analysis code and framework.
  * **Pros:** Access to complete analysis in full detail.
  * **Cons:** Usually hard to decipher 
Input data format may not be consistent (many analyses run on custom-made ntuples). 

* Write your own code:
  * **Pros:** You know exactly what is in the code.  Easy to manipulate.
  * **Cons:**  





{% include links.md %}



