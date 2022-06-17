# FoodRecipeGenerator
Computer Creativity Project
Spring 2022

In this project the text generation methods are utilized to make them able to create food recipes. We processed a dataset which is crawled from a food recipe sharing platform. We experimented Recurrent Neural Network based text generation models on different data configuration to achieve ingredients-to-recipe generation for traditional language models. In addition, we propose a pipeline to fine tune a state-of-art encoder-decoder conditional text generation model PEGASUS and fine-tuned model in order to use it as a recipe generator.

Datasets and pretrained models : https://drive.google.com/drive/folders/1Rz2QPmy9z0n2s9joZ22FJUiolLe2iNnl?usp=sharing

**Entire flow can be tested in Google Colab Environment.**

**The system gives best generation results with PEGASUS Model.**

- **Necessary Installations** and **Assignments** section's cells should run for every attempt in the notebook. The working directory can be changed under this section.

- **Data Processing** creates datasets for training. archive.zip (provided in the Google Drive link) file should be in the current path.

- **For training, provided dataset_1.csv, dataset_2.txt, dataset_3.txt files should be in Data/ directory.**

- **RNN Model Train** section is to train RNN Models, the dataset should be chosen in "Choose dataset" cell. Then Letter or Word approach can be trained.

- **PEGASUS Model Train** section is to fine-tune the PEGASUS model.
-- The output of the train cell of PEGASUS model is to show training is possible only. Since the model takes long to train, it has been reloaded and trained multiple times. The final trained model can be test in TEST section.

TO TEST THE MODELS, AFTER INSTALLATIONS AND ASSIGNMENTS RAN, YOU CAN JUMP TO **TEST** SECTIONS.

You can enter the ingredients by comma seperated and post-processed generated text should be printed in **Generate Recipe** sections.


## Dataset

In this project, the [dataset](https://www.kaggle.com/datasets/shuyangli94/food-com-recipes-and-user-interactions) had been crawled from food.com is re-processed and used for different model training. Ingredients and steps columns of the dataset has been used. Since the project focuses on two different approach of text generation, the data has been prepared to be suitable for these approaches and experiments are handled with multiple pre-process options.
Created dataset formats can be seen in the table below.

| Dataset Version | Training Data                                                                      | Training Pairs          |
|-----------------|------------------------------------------------------------------------------------|-------------------------|
| dataset_1       | X = ”\<sep\>pasta \<sep\>water \<sep\>” y = ”\<sep\>put pasta in water \<sep\>”              | X to y                  |
| dataset_2       | X = ”\<sep\>pasta \<sep\>water \<sep\>  \<sep\>put pasta in water \<sep\>”                   | Try to guess next token |
| dataset_3       | X = ”\<rec\>\<ing\>pasta \<ing\>water \<ing\>  \<s_stp\>\<stp\>put pasta in water \<stp\>\<\/rec\>” | Try to guess next token |

## Models

LSTM based RNN text generation models have been implemented and PEGASUS text summarization model has been fine-tuned to create recipes.

- Letter and Word based generative LSTM models has been train on dataset_2 and dataset_3.
These 4 models has been trained for 50 epochs with 512 batch size for word and 2048 batch size for letter generative models.

- PEGASUS model has been fine-tuned on dataset_1. Encoder and decoder parts has been finetuned for 2 epochs then encoder part has been closed and only decoder part has been fine-tuned for 4 more epochs.


