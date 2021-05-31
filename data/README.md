```sh
.
├── personal_entity # WoW with personal entities
│   ├── ground_truth # 25 WoW dialogues which contains personal entities in each dialogue.
│   │   └── personal_entity_ground_truth.json
│   └── runs
│       ├── personal_entity_rel19-history.json
│       ├── personal_entity_rel19-turn.json
│       ├── personal_entity_tagme-history.json
│       ├── personal_entity_tagme-turn.json
│       ├── personal_entity_wat-history.json
│       └── personal_entity_wat-turn.json
└── sample # Stratified samples
    ├── ground_truth
    │   └── sample_ground_truth.json # Entity annotations from 25 dialogues from each dataset (i.e., MWOZ, QuAC, WoW, and TREC-CAST 2020).
    └── runs
        ├── sample_rel19-history.json
        ├── sample_rel19-turn.json
        ├── sample_tagme-history.json
        ├── sample_tagme-turn.json
        ├── sample_wat-history.json
        └── sample_wat-turn.json
```