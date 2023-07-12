---
title: "Open data reinterpretation with ADL/CutLang"
teaching: 0
exercises: 0
questions:
- "Key question (FIXME)"
objectives:
- "First learning objective. (FIXME)"
keypoints:
- "First key point. Brief Answer to questions. (FIXME)"
---

## Getting prepared for this episode

The exercises here will be run in the CutLang docker container.  Please start it as instructed in [episode 3](.....). 

## A familiar analysis for a new signal

In this exercise, we are going to take the top-antitop quark pair production analysis example you studied in the [simplified analysis example session](https://cms-opendata-workshop.github.io/workshop2023-lesson-ttbarljetsanalysis/) and use it to demonstrate a simple optimized reinterpretation case.  We will modify the analysis selection, so that the analysis becomes sensitive to a new physics scenario, namely, [vector-like quarks](https://lifeandphysics.com/2020/06/15/vector-like-quarks/).

Let's remember the top-antitop quark process, which was the signal in the ttbar analysis:

![](../fig/ttbar_diagram.png){:width="20%"}.

Now let's see our new signal, the vector-like top quark T, in its pair production mode, and with its decays:

![](../fig/VLQ_diagram.png){:width="50%"}.

The vector-like T quark has similar properties with the SM top quark.  For example, it can be pair produced, and decay to bW.  But T can be much heavier.  This opens different decays channels through Z and Higgs boson, as seen in the figure above.  The heavier T gets, the more Lorentz boost its decay products receive.  Our signal is a mixture of all the above decay channels.  We will work with a signal benchmark with T mass = 800 GeV.  We will also check results for two other benchmarks with T mass = 700 and 1200 GeV.

## Exact reinterpretation

What happens if we reinterpreted the top-antitop analysis in terms of the vector-like T model?  Is the analysis sensitive to the vector-like T signal?
In order to find out, we must run the analysis on at least the signal events.  It turns out, our signal events are available in open data, and even in POET format:

| T mass (GeV) | cross section (pb) | OD record | POET ntuple |
|--------|---------------|-----------|-------------|
| 700    |     0.455     | [20232](https://opendata.cern.ch/record/20232) | `RunIIFall15MiniAODv2_TprimeTprime_M-700_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root` |
| 800    |     0.196     | [20233](https://opendata.cern.ch/record/20233) | `RunIIFall15MiniAODv2_TprimeTprime_M-800_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root` |
| 1200   |     0.0118    | [20225](https://opendata.cern.ch/record/20225) | `RunIIFall15MiniAODv2_TprimeTprime_M-1200_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root` |

The POET ntuples have the prefix address: `root://eospublic.cern.ch//eos/opendata/cms/derived-data/POET/23-Jul-22/` (add the root file name to the end).

Next comes the implementation of the analysis.  We already have a version in ADL.  Let's download it to the docker container:

~~~
wget https://raw.githubusercontent.com/ADL4HEP/ADLAnalysisDrafts/main/CMS-TOP-16-006/CMS-TOP-16-001_OD_step1.adl
~~~
{: .language-bash}


> Open the ADL file and see
> * how the object definitions are written
> * how the top candidate is reconstructed
> * how the event selections are done for different regions and how the different regions are related
> * how the histograms are defined.
> What do you think about describing the analysis in this manner?  Is it useful to see all the physics algorithm in one place?
>

Now let's run the ADL file using CutLang over the Tmass = 800 GeV signal for 30000 events:

~~~
CLA root://eospublic.cern.ch//eos/opendata/cms/derived-data/POET/23-Jul-22/RunIIFall15MiniAODv2_TprimeTprime_M-800_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root POET -i CMS-TOP-16-001_OD_step1.adl -e 30000
mv histoOut-ttbarljets.root histoOut-ttbarljets_RunIIFall15MiniAODv2_TprimeTprime_M-800_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root
~~~
{: .language-bash}



~~~
CLA root://eospublic.cern.ch//eos/opendata/cms/derived-data/POET/23-Jul-22/RunIIFall15MiniAODv2_TprimeTprime_M-800_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root POET -i CMS-TOP-16-001_OD_step1.adl -e 30000
mv histoOut-ttbarljets.root histoOut-ttbarljets_RunIIFall15MiniAODv2_TprimeTprime_M-800_TuneCUETP8M1_13TeV-madgraph-pythia8_flat.root
~~~
{: .language-bash}


Look at the text output and the cutflow shown there.  Which cuts reduce the events most?



## Optimized reinterpretation





{% include links.md %}



