Conversational Entity Linking
============

This repository provides the entity linking annotations in conversational settings.

These resources are developed within the following paper:

```
Hideaki Joko, Faegheh Hasibi, Krisztian Balog, and Arjen P. de Vries. “Conversational Entity Linking: Problem Definition and Datasets”.
```

The repository is structured as follows:
- `./data`: MTurk entity annotations data
- `./mturk_interfaces`: MTurk interface used to collect the entity annotations

# Data
Each element in a list has a dict structure as follows:

```py
{ "dialogue_id": "MUL0954.json",
  "dataset_name": "mwoz", # or "quac", "wow", "cast20raw", "cast20manu"
  "turns": [
      {
          "speaker": "USER", # or "SPEAKER"
          "utterance": "Can you tell me if there are any museums in the west part of town?",
          "tool_el_annotations": [
              {
                  "tool": "wat", # or "tagme", "rel19"
                  "method": "turn", # or "history"
                  "mention": "museums",
                  "entity": "Museum"
              },
          ],
          "mturk_el_annotations": [
              {
                  "mention": "town",
                  "entity": "Town",
                  "entity_type": "concept", # or "named_entity"
                  "count_helpful": 2
              },
              {
                  "mention": "museums",
                  "entity": "Museum",
                  "entity_type": "concept",
                  "count_helpful": 2
              }
          ]
      }, ...
    ]
}
```

- dialogue_id: dialogue id provided by each original dataset (i.e., MWOZ, QuAC, WoW, and TREC-CAsT 2020). 
- dataset_name: The name of the dataset in which the conversations were used
- turns: each element contains an user or system turns
  - speaker: USER or SYSTEM
  - utterance: utterance acquired from the dataset. (Note that for TREC-CAST 2020 system turns, only manual_canonical_result_id are shown)
  - tool_el_annotations: annotation with EL tools: WAT, TagMe, and REL
  - mturk_el_annotations: annotations with MTurk workers
    - count_helpful: the number of workers who think the mention-entity pair is helpful to provide a good reply to the user as a system. (max: 3, min: 0)

# MTurk Interfaces

MTurk interface used to collect the entity annotations

Stored in `./mturk_interfaces` directory.

# Conversational Dataset List

[Conversational Dataset List](https://docs.google.com/spreadsheets/d/1N5_5gBKlGR-OrigRNct4jQ6iEqSycyqcoN61JpsHFDQ/edit?usp=sharing): A comprehensive list of around 130 conversational datasets released by different research communities

# TBA
- MTurk interface edit histories with the reasons why those interfaces needed to be modified (based on a pilot experiment on MTurk)

# Contact

If you have any questions, please contact Hideaki Joko at hideaki.joko@ru.nl