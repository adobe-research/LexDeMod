# LexDeMod
Release of LexDeMod and Importance annotation Dataset associated with EMNLP 2022 ([Agent-Specific Deontic Modality Detection on Legal Language](https://aclanthology.org/2022.emnlp-main.795.pdf)) and EMNLP 2023 ([What to Read in a Contract? Party-Specific Summarization of Legal Obligations, Entitlements, and Prohibitions](https://arxiv.org/pdf/2212.09825.pdf)) paper, respectively <br />
*Authors*: [Abhilasha Sancheti](https://abhilashasancheti.github.io/), [Aparna Garimella](https://research.adobe.com/person/aparna-garimella/), [Balaji Vasan Srinivasan](https://research.adobe.com/person/balaji-vasan-srinivasan/), [Rachel Rudinger](http://rudinger.github.io/)  .

1. deontic_data: contains dataset files for the two tasks:
	- Agent-specific Multi-label Classification: The main dataset is in `lease_noisy_removed` folder and  `_et_`, `_est_`, `_est_masked_` folders contain the files used for ablation experiments in Table 4.  `_entity`, and `_entity_random` contains files for the generalization experiments in Table 6.

	- Agent-specific Trigger Span Detection: The main dataset is in `lease_bio_noisy_removed` folder. It contains files used in Table 5. `_entity`, and`_entity_random` contains files for the generalization experiments in Table 6.

	- Similar convention is used for the employment and private lease datasets used in the generalization experiments.
	- Each folder contains train.txt, dev.txt, test.txt files corresponding to each split of the dataset. Folders may contain a tenant and landlord folder in addition with text.txt files for the partitioned dataset. 
	- test_annotated_data.csv and train_eval_annotated_data.csv contains raw annotations collected from the annotators.

2.  importance_data: contains 3 folders
	- ranker: contains train.txt, dev.txt, and test.txt files for the 3 folds used to train and evaluate the importance ranker
		-- each line contains data in the form [PARTY]	sentence1	\</s\>	sentence2	label (0 if sentence1 is more important than sentence2, 1 otherwise)
	- ete: contains ground truth summaries for contracts (end-to-end summarisation) at compression ratios 0.5, 0.10, 0.15 for each fold in the form of a json file.
		-- each json is a list of jsons for 5 contracts; for each contract a ranked list of obligations (obl), entitlements (ent), and prohibitions (pro) is present both for tenant and landlord
	- categorizer: contains train.txt, dev.txt, and test.txt files for the 3 folds used to train and evaluate the content categorizer
		-- each line contains data in the form [PARTY]	sentence	label (list of 1s and 0s indicating the presence or absense of a category)

If you found this repository helpful, please cite our EMNLP 2022, and 2023 papers.
```bibtex
@inproceedings{sancheti-etal-2022-agent,
    title = "Agent-Specific Deontic Modality Detection in Legal Language",
    author = "Sancheti, Abhilasha  and
      Garimella, Aparna  and
      Srinivasan, Balaji Vasan  and
      Rudinger, Rachel",
    booktitle = "Proceedings of the 2022 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2022",
    address = "Abu Dhabi, United Arab Emirates",
    publisher = "Association for Computational Linguistics",
    url = "https://aclanthology.org/2022.emnlp-main.795",
    doi = "10.18653/v1/2022.emnlp-main.795",
    pages = "11563--11579"
}
```
```bibtex
@inproceedings{sancheti-etal-2023-what,
    title = "What to Read in a Contract? Party-Specific Summarization of Legal Obligations, Entitlements, and Prohibitions",
    author = "Sancheti, Abhilasha  and
      Garimella, Aparna  and
      Srinivasan, Balaji Vasan  and
      Rudinger, Rachel",
    booktitle = "Proceedings of the 2023 Conference on Empirical Methods in Natural Language Processing",
    month = dec,
    year = "2023",
}
```