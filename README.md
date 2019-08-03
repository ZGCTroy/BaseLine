# Reproducing
* Baseline 
    | [ResNet50](http://openaccess.thecvf.com/content_cvpr_2016/html/He_Deep_Residual_Learning_CVPR_2016_paper.html)
    | [Network](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/networks/Baseline.py) 
    | [Solver](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/solvers/BaselineSolver.py)
    |
    
* DANN 
    | [Paper](http://www.jmlr.org/papers/volume17/15-239/15-239.pdf)
    | [Network](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/networks/DANN.py)
    | [Solver](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/solvers/DANNSolver.py)
    |


* MT
    | [Paper](https://arxiv.org/abs/1706.05208)
    | [Network](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/networks/MT.py)
    | [Solver](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/solvers/MTSolver.py)
    |
    

* MCD
    | [Paper](http://openaccess.thecvf.com/content_cvpr_2018/html/Saito_Maximum_Classifier_Discrepancy_CVPR_2018_paper.html)
    | [Network](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/networks/MCD.py)
    | [Solver](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/solvers/MCDSolver.py)
    |
    

* MADA
    | [Paper](https://www.aaai.org/ocs/index.php/AAAI/AAAI18/paper/viewPaper/17067)
    | [Network](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/networks/MADA.py)
    | [Solver](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/solvers/MADASolver.py)
    |
   
# Getting Started
## Installation

* Install with pip 
  
        $ pip install torch
    
        $ pip install torchvision
        
        $ git clone https://github.com/ZGCTroy/Domain_Adaptation
        
        $ cd Domain_Adaptation
    
* Install with docker (recommended)

        $ docker pull zgctroy/DA
    
        $ docker run runtime='nvidia' name='zgctory/DA' -it zgctory/DA
    
## Download Datasets
* If you install with docker, you do not have to prepare datasets. As datasets have already been included in docker image.
 
* If you install environment with pip, you have to download datasets by yourself and put them in ./data, and it will look like
    
        - Digits
        -- -- MNIST
        -- -- USPS
        -- -- SVHN
        
        - Office31
        -- -- Amazon
        -- -- Dslr
        -- -- Webcam
        
        - OfficeHome
        -- -- Art
        -- -- Clipart
        -- -- Product
        -- -- Read-World

## RUN
* run Baseline on Digits, from MNIST to USPS

        $ python3.6 main.py --model='Baseline' --dataset='Digits' --source='MNIST' --target='USPS' \
         --cuda='cuda:0' --num_workers=0 --epochs=300 --batch_size=256 --test_interval=1 --optimizer='Adam'
         

* If you want to change the task, the model or any other experiment parameters, you can choose them from the following list.

    * model
    
            $ --model=['Baseline', 'MT', 'DANN', 'MCD','MADA']
    
    * Digits Dataset
    
            $ --source='MNIST' --target='USPS'
            $ --source='USPS' --target='MNIST'
            $ --source='SVHN' --target='MNIST'
    
    * Office31 Dataset
            
            $ --source=['Amazon','Webcam','Dslr']
            $ --target=['Amazon','Webcam','Dslr']
            
    * OfficeHome Dataset
            
            $ --source=['Art','Clipart','Product','Real World']
            $ --target=['Art','Clipart','Product','Real World']
           
    * other parameters
    
        The parameters used in this experiment are shown in [experiments](https://github.com/ZGCTroy/Domain_Adaptation/tree/master/experiments) folder,
        
        for Digits Dataset, we recommend 
        
            $ --optimizer='Adam'
            $ --epoch=300
            $ --batch_size=256
            $ --num_workers=[2,3,4,....]
            $ --test_interval=1
            $ --lr=0.001
            
        for Office31 and OfficeHome Datasets, we recommend
        
            $ --optimizer='SGD'
            $ --iterations=10004
            $ --batch_size=36
            $ --num_workers=0
            $ --test_interval=[100,200,300,...]
            $ --lr=0.001
    