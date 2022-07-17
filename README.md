# Cross-lingual Similarity of Multilingual Representations Revisited

This repository is to reproduce results from our paper: Cross-lingual Similarity of Multilingual Representations Revisited.

## Notebook with results (start here):

[Notebook: Cross-lingual Similarity of Multilingual Representations Revisited](anc/results.ipynb)


## Installation
```

conda create -n anc python=3.8
conda activate anc

pip install torch 
pip install scipy, pandas, matplotlib
conda install -c conda-forge notebook

pip install transformers
pip install datasets

pip install ecco

pip install -U sacremoses
pip install sentencepiece
pip install protobuf

```

## Fetch data

```bash
mkadir assets
mkdir experiments
cd experiments
mkdir multilingual
cd multilingual  

# xnli extension
mkdir xnli_extension
git clone https://github.com/salesforce/xnli_extension xnli_ext_repo
mv xnli_ext_repo/data xnli_extension
rm -rf xnli_ext_repo

# xnli 15way
mkdir xnli_15way
wget https://dl.fbaipublicfiles.com/XNLI/XNLI-15way.zip
unzip XNLI-15way.zip
rm XNLI-15way.zip
mv XNLI-15way xnli_15way/data

cd ../..
```

Run the following from ```anc``` directory.

## XLM-R Normformer Experiments

Pretraining models are coming soon!

```bash
python -u encode_dataset_with_models.py norm_1M

python -u run_analysis.py norm_1M cka
python -u run_analysis.py norm_1M acc 
python -u run_analysis_torch_corr.py norm_1M corr
```

## ANC Scaling Laws for Meta XLM-R and XGLM Models

```bash
python -u encode_dataset_with_models.py xlmr
python -u encode_dataset_with_models.py xglm

python -u run_analysis_torch_corr.py xlmr corr
python -u run_analysis_torch_corr.py xglm corr
```

## Results

Now you can run the analysis from the [Notebook](anc/results.ipynb).
