# Targeted Adversarial Attack against Multimedia Recommender Systems (***TAaMR***)

GitHub repository of the DMSL2020 paper: **Targeted Adversarial Attack against Multimedia Recommender Systems**, published by Tommaso Di Noia, daniele Malitesta and Felice Antonio Merra.

The architectural overview of the proposed approach is as below:
![***TAaMR***](https://github.com/sisinflab/TAaMR/blob/master/Overview.png)


### Data preparation
To run the experimental section it is necessary to:
* Create in ```./data/``` a directory to store the dataset.
* Move in ```./data/<dataset_name>/```.
* Insert train and test file ```user_id\titem_id``` (users' and items indices need to be from 0 to N-1).
* Create directory ```./data/<dataset_name>/original_images/images/```.
* Store in ```./data/<dataset_name>/original_images/images/``` all the images using the same ```item_id``` in the format ```item_id.jpg```.

### Experiments
Operations to be executed (in ```src/```):
* ```classify_extract.py``` - Executes the classification and the feature extraction on original images (the files ```classes.csv``` and ```features.npy``` are stored in ```./data/<dataset_name>/original_images/```).
* ```rec_generator.py``` - Generates the recommendation for the clean classes.
* ```results_analyzer.py``` - Evaluates the recommendation lists useful for select the origin and target class for the **targeted adversarial attack**.

### Results evaluation
For the generation of each attack, run the script ```classify_extract_attack.py```. It will create a new directory named ```./data/<dataset_name>/<attack_name_parameters>/```.

After each attack, run again ```rec_generator.py``` and ```results_analyzer.py``` to generate the new recommendations and evaluate these results. Additionally, run ```evaluate_visual_images.py``` to evaluate the visual metrics on the attacked images. 

### Implemented attacks
* FGSM 
* PGD


### Requirements

* Python 3.6.8
* CUDA 10.1
* cuDNN 7.6.4

All the requirements are in the file ```requirements.txt```

```
pip install -r requirements.txt
```
***

If you use this code, please cite us:

```
@INPROCEEDINGS{DBLP:conf/dsn/DiNoia20,
    author={T. {Di Noia} and D. {Malitesta} and F.A. {Merra}}, 
    booktitle={the 50th Annual IEEE/IFIP International Conference on Dependable Systems and Networks Workshops (DSN-DSML'20)}, 
    title={TAaMR: Targeted Adversarial Attack against Multimedia Recommender Systems},
    year={2020}
    }
```
