# Targeted Adversarial Attack against Multimedia Recommender Systems (***TAaMR***)

GitHub repository of the DMSL2020 paper: **Targeted Adversarial Attack against Multimedia Recommender Systems**, published by Tommaso Di Noia, Daniele Malitesta and Felice Antonio Merra.

Paper available at [Sisinflab](http://sisinflab.poliba.it/publications/2020/DMM20/) publications web page.

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
@InProceedings{DMM20,
author = {Tommaso {Di Noia} and Daniele Malitesta and Felice Antonio Merra},
    title = "TAaMR: Targeted Adversarial Attack against
    Multimedia Recommender Systems",
    booktitle = "The 3rd International Workshop on Dependable and
    Secure Machine Learning – DSML 2020 Co-located
    with the 50th IEEE/IFIP International Conference
    on Dependable Systems and Networks (DSN 2020)",
    series = "2020",
    year = "2020",
    publisher = "IEEE Digital Library",
    organization = "IEEE",
    keywords = "Adversarial Machine Learning, Recommender Systems",
    url = "http://sisinflab.poliba.it/publications/2020/DMM20"
}
```
