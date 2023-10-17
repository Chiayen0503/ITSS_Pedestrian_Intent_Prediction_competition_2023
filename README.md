# Overview of data preprocessing and modelling
This is an introduction of how to navigate the following folders and their functionality. You can download all folders, trained weights and preprocessed data in just one link: https://drive.google.com/drive/folders/1P03UYafoWcOuTDXKd0C5kAi1-aR4z35q?usp=share_link)
* (1) PSI-Dataset/
* (2) tf-cpn/
* (3) JAAD/
* (4) PSI-competition/
* (5) stacking/ 

## Data preparation
### 1. To begin with data preparation, first clone and extract annotations from `PSI-Dataset/`
```
git clone https://github.com/PSI-Intention2022/PSI-Dataset.git
```
* follow `README.md` to extract annotations
* download and extract notebooks and .py programmes from `PSI-Dataset_notebooks.zip`. <br>
(link: https://drive.google.com/file/d/1hwDpJsn8QbCjiAXPXqgCsTQC0COk2KAI/view?usp=share_link) <br>
Move them to `PSI-Dataset/` and run the notebooks in order. 

### 2. use `tf-cpn/` to extract keypoints from a given `cropped_bboxes/` from either (1), (3) or (4). We will process all of them. <br>
(See `3. generate keypoints for PSI-Dataset.ipynb` in `PSI-Dataset/` to prepare `tf-cpn/` folder.)
### 3. merge `cropped_bboxes/` and labels from (3) to (1) and create a bigger train set in (1)
(See `8. get preprocessed train and validation data.ipynb` in `PSI-Dataset/`)
### 4. create validation set in (1) <br>
(See `8. get preprocessed train and validation data.ipynb` in `PSI-Dataset/`)
### 5. create test set in (4) <br> 
(See `9. get preprocessed test data.ipynb` in `PSI-Dataset/`)
### 6. before train/val/test the models in  `stacking/`, download stacking folder (see next section) and move the following folders to `stacking/preprocessed_data/`
* `train/` and `val/` from `preprocessed_data/` in (1)
* `test/ ` from `preprocessed_data/` in (4)

## Training/Testing models
### 1. Download stacking folder from the following link:
https://drive.google.com/file/d/1AVFUuSbWzwR7PgbXQXQUz-Cf09pR-r1H/view?usp=sharing

### 2. For convenience purpose, skip data preparation by downloading `preprocessed_data.zip` from the following link:
https://drive.google.com/file/d/10GZe4BUoku2UG70PdsJScfa5n4TAsI_o/view?usp=sharing

and place `preprocessed_data/` in `stacking/`
### 4. run the notebooks with title number `1.`, `2.` and `3.` in `stacking/` to train two classification models and an ensemble model. Trained models will be saved to `training_results/best_val_f1/`
### 5. alternatively, download trained weight zip (`best_val_f1.zip`) from the following link and extract and put it in `training_results/`
link: https://drive.google.com/file/d/1nM6eaMjcapZldPuE-MGS7nk1m48hc_7u/view?usp=sharing
### 6. run the notebooks with title number `4.` and `5.` in `stacking/` to get the final validation and test predictions. 

### the outline of directory is like this:
    .
    ├── PSI-Dataset/       #PSI train/val          
    ├── tf-cpn/            #keypoint generator             
    ├── JAAD/              #JAADbeh train (will merge with PSI train)                
    ├── PSI-Competition/   #PSI test                  
    ├── stacking/          #model training and testing
    └── Overview.md

## Performance
The work has won the 1st Prize in ITSC ITSS student competition in the 1st track of Pedestrian Behaviour Prediction (link: https://psi-intention2022.github.io/). The following table shows its performance on predicting PSI validation set and test set. 

<td>

Dataset | Accuracy | Mean class accuracy | Macro-F1 
---|---|---|---
PSI val |69.9%| 64.9% | 63.2%
PSI test |70.1% | 63.3% | 62.3%

</td>
</tr>
</p>
