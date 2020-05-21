# Mask_Helmet_Classification
The repo contains the solution to the problem given for the interview.

## Data

* Crops of faces were used as the input for training.
* The data collected from internet sources was used for training/validation as 90-10 split.
* The data provided was used as unseen testing data.
* Data preprocessing :- <br \>
  1. Resize to 224x224
  2. Mean Normalization

## Training      

* Training procedure followed for **Mask/NoMask** and **Helmet/NoHelmet** classification training

  1. Load face crops in dataloader
  2. Forward pass on the model
  3. Calculate cross entropy loss
  4. Continue from step 1, if validation loss is decreasing
  5. Convergence - Termination
  
|                          |            |          
|--------------------------|------------|
|**Model  Architecture**   | Resnet18   |
|**Framework**             | PyTorch    |
|**Trainable Parameters**  | 11 Million |
|**Batch Size**            | 128        |
|**Number of epochs**      | 100        |
|**Online Augmentations**  | Yes        |

**Output** : Two models , one for mask/nomask classification and another for helmet/nohelmet classification
[Trained Models --> Link!](https://drive.google.com/open?id=1tk-lnsovJGBLGTlYRxLIMFtKAoB6NiVD)

**Note** I used an open source framework written in PyTorch by Ross Wightman for training these models.

## Commands

### Inference

* This script gives you label prediction for the image(s) given and has an option of dumping
the results in their respective label folder in the given result dir.

`python3 inference.py DATA_PATH --model resnet18 --checkpoint MODEL_PATH --result_dir RESULT_DIR`

### Validation

* This script will calculate the top1 accuracy of the model. 
* **Top1 accuracy** determines the best matched label for your image(s).  
I chose calculate top1 accuracy metric as it is intuitive for analysis of classification tasks based models.

`python3 validate.py DATA_PATH --model resnet18 --checkpoint MODEL_PATH`

## Results

|      |Validation| Test  |
|------|----------|-------|
|Mask  |    94.4  |  93.7 |
|Helmet|    94    |  85.6 |

The results for above model for validation and test sets can be found at this --> [link!](https://drive.google.com/open?id=1CvlAL7A8ihzesiWaig6LnArqV9B3Kf8v)
