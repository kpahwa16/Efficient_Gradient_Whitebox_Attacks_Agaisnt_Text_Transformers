# CS269_Final_Project
Computationally Efficient Gradient Based Whitebox Attacks against Text Transformers


## Abstract

Deep learning models are now widely deployed in safety critical, medical, and other security demanding application environments, and are becoming highly ubiquitous. Thus there is an ever-increasing concern about the vulnerabilities of these models and their susceptibility to adversarial attacks. Most of the adversarial attacks studied in prior literature have focused on computer vision applications because the perturbation space is continuous, and thus gradient based optimization problems can be solved. However, extending this to text is not trivial because of the discrete attack space. In this paper, we attempt to reduce the computational complexity involved in gradient based whitebox attack against a gpt2 model pre-trained on the downstream NLP tasks of news categorization of the AG News dataset, and natural language inference on the MNLI dataset. Particulary, we attempt to attain performance increases in attacking the text samples while maintaining a high average semantic similarity in the adversarial output text, along with a high degree of imperceptibility. 


## Installation Steps

```
git clone https://github.com/kpahwa16/CS269_Final_Project.git
cd CS269_Final_Project
conda env create --file=env_attack.yml
conda activate attack

```

## Finetuning the pre-trained transformer gpt2 model on a specific dataset ("ag_news, yelp, mnli")

```
python model_finetune.py --dataset {specify dataset_name, mandatory} --result_folder {specify result folder path to save the finetuned model file,'mandatory'} --checkpoint_folder {specify checkpoint folder path to save the various checkpoints, 'optional'} --batch_size {specify the batch size, 'optional'} --epochs {specify the epochs, 'optional'}  <br />

Eg. python model_finetune.py --dataset ag_news

### Note: optional arguments would take the default values


```
