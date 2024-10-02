# MolLEO

## About

MolLEO is an LLM-augmented evlotuionary algorithm for molecular discovery!


## Setups
You need to get an OpenAI API key for GPT-4. BioT5 is an open-source language model which can work on either GPU or CPU.

### Package Installation
```bash
conda create -n molleo python=3.9
conda activate molleo
conda install pytorch==2.1.2 torchvision==0.16.2 torchaudio==2.1.2 pytorch-cuda=12.1 -c pytorch -c nvidia
pip install PyTDC 
pip install PyYAML
pip install rdkit
pip install transformers
pip install sentencepiece
pip install selfies
```

Then we can activate conda via following command. 
```bash
conda activate molleo 
```


### Experiments
The experiments are conducted on the following categories: `single obejective optimization` and `multi objective optimization`.

To run experiments on single objective optimization task:

```bash
cd single_objective
# BioT5 on jnk3 task
python run.py molleo --mol_lm BioT5 --oracles jnk3 --seed 1 2 3
# GPT-4 on gsk3b task
python run.py molleo --mol_lm GPT-4 --oracles gsk3b --seed 1 2 3
```
To run experiments on multi objective optimization task:

```bash
cd multi_objective
# objective summation on task 1
python run.py molleo_multi --mol_lm BioT5 --min_obj sa --max_obj jnk3 qed --seed 1 2 3
# pareto optimal set selection on task 2
python run.py molleo_multi_pareto --mol_lm GPT-4 --min_obj sa --max_obj gsk3b qed --seed 1 2 3
# pareto optimal set selection on task 3
python run.py molleo_multi_pareto --mol_lm GPT-4 --min_obj sa gsk3b drd2 --max_obj jnk3 qed --seed 1 2 3
```
