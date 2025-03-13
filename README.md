# Translation Quality Management

This repository presents a translation quality management system (TQMS) based upon international standards by technical committee ASTM F43 on Language Services and Products.

## Assumptions

### Standards-Based Approach to Translation

The workflow and materials presented in this repository follow best practices outlined in the following ASTM F43 standards:

- F2575 Standard Practice for Language Translation
- WK46396 Practice for Analytic Evaluation of Translation Quality (MQM) (draft standard)
- WK54884 Holistic Quality Evaluation System for Translation (H-Quest) (draft standard)

According to F2575, translation projects must begin with the definition of specifications (requirements, outcomes) and it is recommended that a translation > editing > proofreading (TEP) workflow be followed. WK46396 presents a methodology for identifying translation errors based on the [MQM typology](https://themqm.org/the-mqm-typology/) to carry out preventative and corrective action. WK54884 presents a methodology for evaluating the quality of a translation as a whole document, in contrast to the decontextualized sentence-by-sentence approach that is the status quo of translation technology. This repository combines the MQM and H-Quest methodologies in evaluating translation quality.

### Technology

In status quo workflows, translation quality evaluations take place in translation tools in which source and target content is subdivided into decontextualized matching sentence pairs. The workflow presented in this repository specifically departs from that approach. Rather than presenting texts for sentence-by-sentence evaluation in a translation technology environment, whole texts are presented for evaluation within [Label Studio](https://labelstud.io) for this implementation. This whole text approach allows for a contextualized quality evaluation to take place.

To annotate texts within Label Studio, a `label_config` file presenting the annotation methodology is required. The current iteration of the `label_config` file based on MQM and H-Quest that is being used within this project is shared within this repository.

Note: In this labeling configuration, the following adjustments have been made to the current implementation of the MQM Core Typology:
- Textual Conventions have been moved from the Linguistic Conventions to the Style dimension. That categorization made more sense to me, since a text should match the style of its particular text type.
- Unidiomatic Style and Awkward Style have been combined into one error: Unnatural Style. This avoids issues with differentiating between these two error types.

### Starting Point

At first translation quality evaluators marking errors according to MQM (or any error typology) will do so inconsistently. This is because people view quality subjectively and an optimal error categorization is often not immediately clear. By using tools like visualizations and scoring, we can see where ideas don't overlap and work toward a harmonized performance.

### Outcomes

The workflow presented in this repository has the purpose of training translation evaluators/annotators to produce high quality annotated texts for use in:
- To be able to give feedback that will help translators improve
- To be able to identify, correct and prevent common issues
- In the age of generativeAI, to produce high quality labeled data that can be used to teach the machines to identify and produce translations that are free from labeled errors. With high quality annotated data, the machines can be taught to identify labeled errors when carrying out automatic post editing and to produce translations free from labeled errors at the automatic translation stage.

### Workflow

- An evaluation project is set up in Label Studio that uses the MQM/H-Quest labeling configuration
- A group of translation evaluators evaluate texts within Label Studio
  - They mark individual errors following MQM
  - They rate the quality of the content as a whole in terms of correspondence to the source text and readability as a standalone document given the proejct specifications following H-Quest
- JSON-MIN files of their work is exported and processed within the Jupyter notebook provided
- Within the Jupyter notebook, JSONs are pre-processed, exploratory analysis takes place, and performance around exact matching, F1 for partial matching, and Kappa for category agreement are calculated
- Based upon the results determined via Jupyter analysis, an improvement plan that prioritizes the highest priority changes is implemented (i.e. training materials, discussions)
- The work continues in this way until the annotations by a group of evaluators reaches the minimum threshold scores for exact matching, F1 for partial matching, and Kappa for category agreement
- The evaluators are then deployed to produce annotations that will be used to produce the outcomes identified above.

### Folder Structure
```
translation-quality-mgmt/
├── setup/
│   ├── for_annotation/          # Target contents prepared in JSON format based on a whole-document presentation for upload to Label Studio
│   ├── label_config/            # Label configuration file based on MQM/H-Quest used as the basis for labeling in Label Studio
├── translation-annotations/                    
│   ├── annotations/             # Exported JSON-MIN files from the Label Studio environment that contain the annotations by translation evaluators
│   ├── notebooks/               # Jupyter notebooks of translation annotator agreement analysis
├── references/                  # Source content presented within the contextualization of the original formatting, specifications, style guides, glossaries, etc.
```

## References

- [The MQM Core Typology](https://themqm.org/the-mqm-typology/)
- ASTM F2575-23e2, Standard Practice for Language Translation
- ASTM WK46396, Practice for Analytic Evaluation of Translation Quality (draft standard)
- ASTM WK54884, Holistic Quality Evaluation System for Translation (draft standard)

## License
This repository is currently licensed under GPL-2.0 license.

## GAI Disclaimer & Acknowledgement
The notebook presented in this repo was developed using Claude 3.5 Sonnet. Please review the code thoroughly before integrating it into your implementation.

