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
@inproceedings{DBLP:conf/dsn/NoiaMM20,
  author    = {Tommaso Di Noia and
               Daniele Malitesta and
               Felice Antonio Merra},
  title     = {TAaMR: Targeted Adversarial Attack against Multimedia Recommender
               Systems},
  booktitle = {50th Annual {IEEE/IFIP} International Conference on Dependable Systems
               and Networks Workshops, {DSN} Workshops 2020, Valencia, Spain, June
               29 - July 2, 2020},
  pages     = {1--8},
  publisher = {{IEEE}},
  year      = {2020},
  url       = {https://doi.org/10.1109/DSN-W50199.2020.00011},
  doi       = {10.1109/DSN-W50199.2020.00011},
  timestamp = {Mon, 03 Aug 2020 17:18:56 +0200},
  biburl    = {https://dblp.org/rec/conf/dsn/NoiaMM20.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```
