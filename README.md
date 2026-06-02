# Ukrainian-NER

This repository contains the experimental pipeline used for a bachelor thesis on named entity recognition (NER) for the Ukrainian language using large language models.

The published version focuses on **MamayLM 9B** and the **NER-UK 2.0** dataset. The task is formulated as a generative text transformation problem: the model receives a Ukrainian text fragment and returns the same text with inline entity tags in the format:

```text
[TYPE: entity]
```

For example:

```text
[PERS: Тарас Шевченко] народився в [LOC: Україні].
```

## Repository scope

During the thesis work, several similar pipelines and notebooks were created for different models. To keep this repository compact, only the pipeline for **MamayLM 9B with a GEPA-tuned prompt** is published here.

The repository includes:

* dataset preprocessing and normalization;
* conversion of Brat Standoff annotations into inline generative NER format;
* dataset chunking for training and evaluation;
* QLoRA fine-tuning of MamayLM 9B with the standard prompt;
* evaluation with both the standard prompt and the GEPA-tuned prompt;
* extraction of predicted entities from generated text;
* calculation of precision, recall, and F1-score;
* GEPA prompt tuning.

## Note about GEPA

GEPA was used only for **prompt optimization**.
The model was **not fine-tuned with GEPA itself**.

The fine-tuning procedure uses QLoRA on MamayLM 9B. The GEPA-tuned prompt is used as an alternative evaluation prompt to compare how prompt formulation affects generative NER quality.

## Dataset

The experiments are based on **NER-UK 2.0**, a manually annotated Ukrainian named entity recognition corpus. The original Brat Standoff annotations are converted into a generative inline-tagging format.

## Model

The main model used in the published pipeline is:

```text
INSAIT-Institute/MamayLM-Gemma-2-9B-IT-v0.1
```
