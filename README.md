ConEL: Conversational Entity Linking Datasets
============

This repository provides the resources related to entity linking annotations in conversational settings.\
These resources are created on the existing datasets:
- [MultiWOZ](https://github.com/budzianowski/multiwoz) (MWOZ)
- [Question Answering in Context](https://quac.ai/) (QuAC), 
- [Wizard-Of-Wikipedia](https://parl.ai/projects/wizard_of_wikipedia/) (WoW)
- [TREC-CAsT 2020](https://github.com/daltonj/treccastweb)

These resources are developed within the following paper:
- *Hideaki Joko, Faegheh Hasibi, Krisztian Balog, and Arjen P. de Vries. “[Conversational Entity Linking: Problem Definition and Datasets](https://arxiv.org/abs/2105.04903)”.*


The repository is structured as follows:
- `./data`: MTurk entity annotations
- `./mturk_interfaces`: MTurk interface used to collect the entity annotations

# Data

MTurk entity annotation data is stored in `./data`.
- `./data/sample/`: Stratified samples
  - `./data/sample/ground_truth/sample_ground_truth.json`: Entity annotations from 25 dialogues from each dataset (i.e., MWOZ, QuAC, WoW, and TREC-CAST 2020).
- `./data/personal_entity/`: WoW with personal entities
  - `./data/personal_entity/ground_truth/personal_entity_ground_truth.json`: 25 WoW dialogues which contains personal entities in each dialogue.
- `run` folders contain EL tools' results

## Statistics

|                   | Stratified samples<br>(./data/sample/) | WoW with personal entities<br>(./data/personal_entity/) |
|-------------------|----------------------------------------|---------------------------------------------------------|
| # dialogues       | 100                                    | 25                                                      |
| # user utterances | 708                                    | 113                                                     |


## Data Format
This section explains ground truth files data format (`sample_ground_truth.json` and `personal_entity_ground_truth.json`)\
Each element in a list has a dict structure as follows:

```py
{
    "dialogue_id": "10060",
    "dataset_name": "wow", # or "quac", "mwoz", "cast20raw", "cast20manu"
    "turns": [
        {
            "speaker": "USER", # or "SYSTEM"
            "utterance": "Blue is my favorite color, by far. What's yours?",
            "turn_number": 0, 
            "el_annotations": [ # Ground truth annotations
                {
                    "mention": "Blue",
                    "entity": "Blue",
                    "entity_type": "concept", # or "named_entity"
                }
            ],
            "personal_entity_annotations": [ # Personal entity annotations
                {
                    "personal_entity_mention": "my favorite color",
                    "explicit_entity_mention": "Blue",
                    "turn_number_of_explicit_entity_mention": 0,
                    "entity": "Blue"
                }
            ]
        },
    ]
}
```

- `dialogue_id`: dialogue id provided by each original dataset (i.e., MWOZ, QuAC, WoW, and TREC-CAsT 2020). 
- `dataset_name`: The name of the dataset in which the conversations were used (cast20raw and cast20manu represent )
- `turns`: each element contains an user or system turns
  - `speaker`: USER or SYSTEM
  - `utterance`: utterance acquired from the dataset. (Note that for TREC-CAST 2020 system turns, only manual_canonical_result_id are shown)
  - `el_annotations`: annotations with MTurk workers
  - `personal_entity_annotations`: Personal entity annotations. Note that only `wow_with_personal_entities.json` has this annotations.

# MTurk Interfaces

MTurk interface used to collect the entity annotations.\
Interfaces are Stored in `./mturk_interfaces` directory.

# Conversational Dataset List

[Conversational Dataset List](https://docs.google.com/spreadsheets/d/1N5_5gBKlGR-OrigRNct4jQ6iEqSycyqcoN61JpsHFDQ/edit?usp=sharing): A comprehensive list of around 130 conversational datasets released by different research communities

<!--# TBA
MTurk interface edit histories with the reasons why those interfaces needed to be modified (based on a pilot experiment on MTurk)-->

# Cite

```bibtex
@inproceedings{Joko:2021:CEL,
 author =    {Joko, Hideaki and Hasibi, Faegheh and Balog, Krisztian and de Vries, Arjen P.},
 title =     {Conversational Entity Linking: Problem Definition and Datasets},
 booktitle = {Proceedings of the 44rd International ACM SIGIR Conference on Research and Development in Information Retrieval},
 series =    {SIGIR '21},
 year =      {2021},
 publisher = {ACM}
}
```

# Contact

If you have any questions, please contact Hideaki Joko at hideaki.joko@ru.nl
