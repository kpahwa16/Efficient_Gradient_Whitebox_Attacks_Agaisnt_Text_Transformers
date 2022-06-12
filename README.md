# CS269_Final_Project
Computationally Efficient Gradient Based Whitebox Attacks against Text Transformers


## Abstract

Deep learning models are now widely deployed in safety critical, medical, and other security demanding application environments, and are becoming highly ubiquitous. Thus there is an ever-increasing concern about the vulnerabilities of these models and their susceptibility to adversarial attacks. Most of the adversarial attacks studied in prior literature have focused on computer vision applications because the perturbation space is continuous, and thus gradient based optimization problems can be solved. However, extending this to text is not trivial because of the discrete attack space. In this paper, we attempt to reduce the computational complexity involved in gradient based whitebox attack against a gpt2 model pre-trained on the downstream NLP tasks of news categorization of the AG News dataset, and natural language inference on the MNLI dataset. Particulary, we attempt to attain performance increases in attacking the text samples while maintaining a high average semantic similarity in the adversarial output text, along with a high degree of imperceptibility. 


## Installation Steps

Install conda and run the steps below:

```
$ git clone https://github.com/kpahwa16/CS269_Final_Project.git
$ cd CS269_Final_Project
$ conda env create --file=env_attack.yml
$ conda activate attack

```

## Finetuning the pre-trained transformer gpt2 model on a specific dataset ("ag_news, yelp, mnli")
The source code to fine-tune GPT-2 model from HuggingFace for a classification task is available at ./Finetuning folder. 

```
$ python model_finetune.py --dataset {specify dataset_name, mandatory} --result_folder {specify result folder path to save the finetuned model file,'mandatory'} --checkpoint_folder {specify checkpoint folder path to save the various checkpoints, 'optional'} --batch_size {specify the batch size, 'optional'} --epochs {specify the epochs, 'optional'}  <br />

For example, to fine-tune GPT-2 moel on AG News dataset for news categorization, run:

$ python model_finetune.py --dataset ag_news


### Note: optional arguments would take the default values


```
After training, the fine-tuned model gpt2_ag_news_finetune.pth will be saved in the result folder.


## Attacking the finetuned model (3 choices: gbda_attack, gradient_projection_attack, synonym_distribution_attack)

To attack a finetuned model trained in the previous step, run the following source code available at ./Attack:

```
# for running the gbda attack, run:

$ python gbda_attack.py  --start_index {specify start index}  --num_samples {specify num samples} --dataset {specify the dataset}

For eg. to attack 100 samples of ag_news dataset starting from index 0, run:

$ python gbda_attack.py  --start_index 0  --num_samples 100 --dataset ag_news

# for running the gradient projection attack (L2L1 sparsity / Block Sparsity), run :

$ python gradient_projection_attack.py  --start_index {specify start index}  --num_samples {specify num samples} --dataset {specify the dataset}

# for running the synonym distribution attack, run:

$ python synonym_distribution_attack.py  --start_index {specify start index}  --num_samples {specify num samples} --dataset {specify the dataset}

```
After running this code, a pickle file of the results are generated and saved in the results folder (specified in the previous step)

### Evaluating the Attack 


To evaluate the attack, run the following source code available at ./Attack:

```
# for evaluating the gbda attack, run:

$ python evaluate_attack.py  --start_index {specify the start index} --num_samples {specify the num of samples to attack} --dataset {specify the dataset}

# Note: Please ensure to provide the exact same --start_index and --num_samples used in the previous stage to attack the finetuned gpt2 model, this is 

because it would be used to load the pickle file having the format start_index_end_index_dataset.pkl . If this is not specified correctly,

then the pickle file would not be loaded for evaluation.


```




