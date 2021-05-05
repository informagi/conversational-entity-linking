ConvEL: Conversational Entity Linking Datasets
============

This repository provides the resources related to entity linking annotations in conversational settings.\
These resources are created on the existing datasets:
- [MultiWOZ](https://github.com/budzianowski/multiwoz) (MWOZ)
- [Question Answering in Context](https://quac.ai/) (QuAC), 
- [Wizard-Of-Wikipedia](https://parl.ai/projects/wizard_of_wikipedia/) (WoW)
- [TREC-CAsT 2020](https://github.com/daltonj/treccastweb)

These resources are developed within the following paper:

```
Hideaki Joko, Faegheh Hasibi, Krisztian Balog, and Arjen P. de Vries. “Conversational Entity Linking: Problem Definition and Datasets”.
```

The repository is structured as follows:
- `./data`: MTurk entity annotations
- `./mturk_interfaces`: MTurk interface used to collect the entity annotations

# Data
MTurk entity annotation data is stored in `./data`: 
- `samples.json`: Entity annotations from 25 dialogues from each dataset (i.e., MWOZ, QuAC, WoW, and TREC-CAST 2020).
- `wow_with_personal_entities.json`: 25 WoW dialogues which contains personal entities in each dialogue.

## Statistics

|                   | Stratified samples<br>(sample.json) | WoW with personal entities<br>(wow_with_personal_entities.json) |
|-------------------|-------------------------------------|-----------------------------------------------------------------|
| # dialogues       | 100                                 | 25                                                              |
| # user utterances | 708                                 | 113                                                             |


## Data Format
Each element in a list has a dict structure as follows:

```py
{
    "dialogue_id": "10060",
    "dataset_name": "wow", # or "quac", "mwoz", "cast20raw", "cast20manu"
    "turns": [
        {
            "speaker": "USER", # or "SYSTEM"
            "utterance": "Blue is my favorite color, by far. What's yours?",
            "tool_el_annotations": [
                {
                    "tool": "wat", # or "tagme", "rel19"
                    "method": "history", # or "turn"
                    "mention": "Blue",
                    "entity": "Blue"
                },
            ],
            "mturk_el_annotations": [
                {
                    "mention": "Blue",
                    "entity": "Blue",
                    "entity_type": "concept", # or "named_entity"
                    "count_helpful": 2 # From 0 to 3
                }
            ],
            "mturk_personal_entity_annotations": [
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
  - `tool_el_annotations`: annotation with EL tools: WAT, TagMe, and REL
  - `mturk_el_annotations`: annotations with MTurk workers
    - `count_helpful`: the number of workers who think the mention-entity pair is helpful to provide a good reply to the user as a system. (max: 3, min: 0)
  - `mturk_personal_entity_annotations`: Personal entity annotations. Note that only `wow_with_personal_entities.json` has this annotations.

# MTurk Interfaces

MTurk interface used to collect the entity annotations.\
Interfaces are Stored in `./mturk_interfaces` directory.

# Conversational Dataset List

[Conversational Dataset List](https://docs.google.com/spreadsheets/d/1N5_5gBKlGR-OrigRNct4jQ6iEqSycyqcoN61JpsHFDQ/edit?usp=sharing): A comprehensive list of around 130 conversational datasets released by different research communities

<!--# TBA
MTurk interface edit histories with the reasons why those interfaces needed to be modified (based on a pilot experiment on MTurk)-->

# Contact

If you have any questions, please contact Hideaki Joko at hideaki.joko@ru.nl
