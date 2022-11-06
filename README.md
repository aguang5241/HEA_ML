# High-Entropy Materials Design by Integrating the First-Principles Calculations and Machine Learning: a Case Study in the Al-Co-Cr-Fe-Ni System

## Overview
The first-principles calculation is widely used in high-entropy materials. However, this approach may consume many computational resources for complex systems, limiting the construction of property maps for the corresponding materials over a full composition range. In this work, the most common Al-Co-Cr-Fe-Ni system (both FCC and BCC) is selected for our investigation. We formulate a materials design strategy that combines first-principles calculation results and machine learning models to establish a robust database of properties (e.g., phase stabilities and elastic constants): starting from unary, binary, ternary, and quaternary, then extending into high-order systems. Analyzing and screening this database can further inspire discovering and designing new high entropy materials. Moreover, the corresponding software was developed to facilitate the use of related persons or institutions.

## Workflow
* Above the iceberg:  
The training data of properties (e.g., phase stabilities and mechanical properties) is obtained by the first-principles calculation. The rules lying behind the data can be discovered by machine learning.
* Below the iceberg:  
The knowledge of HEA over a full composition range can be obtained from well-trained model, and the corresponding software is developed with the knowledge embedded.

    <div align=left><img src='./res/demo0_graphical_abstract.png' alt='' width='700'/></div>

## Get Started
### Download
* Visit https://github.com/aguang5241/HEA_ML/releases to download the demo version of software (Windows, MacOS are supported). *Note: The demo version of software is only for demonstration purpose. It is not intended for commercial use. For full version of software, please contact us (gliu4@wpi.edu; yzhong@wpi.edu)*.

### Usage Description
1. Two search modes are available: *Single-Point* and *Advanced*.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.7_Software.jpg' alt='' width='700'/></div>

2. On the *Single-Point* page, you can calculate the predicted properties based on the exact given concentration.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/single.gif' alt='' width='700'/></div>

3. On the *Advanced* page, you can calculate and analyze the predicted properties based on certain given conditions.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/advanced.gif' alt='' width='700'/></div>

## Main Results
### Modeling
* This work uses the latest hyperparameter optimization framework, OPTUNA, to perform automated algorithm-driven ML model tuning. The detailed search space of the hyperparameters involved is listed in the table below.

    | Objectives | Search space |
    | :--- | :--- |
    | Trials number | 0 ~ 500 |
    | Number of layers | 2 ~ 6 |
    | Number of nodes | 100 ~ 300 |
    | Learning rate | 0.0001 ~ 0.01 |
    | Weight decay | 0.00001 ~ 0.001 |
    | Optimizer | Adam, SGD, RMSprop |

* Results of algorithm-driven modeling: (a) optimization history; (b) importance plot for difference hyperparameters; and (c) detailed optimization results based on specific hyperparameters.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.1_Modeling.jpg' alt='' width='700'/></div>

### Training
* The training data of properties (e.g., phase stabilities and mechanical properties) is obtained by the first-principles calculation. The rules lying behind the data can be discovered by machine learning. Analysis of R-values for $C_{11}$ of the BCC with progressive training: (a) unary training and binary testing; (b) unary + binary training and ternary testing; and (c) unary + binary + ternary training and quaternary testing; (d) finalization of the model.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.2_Training.jpg' alt='' width='700'/></div>

### Prediction
* The knowledge of HEA over a full composition range can be obtained from well-trained model, and the corresponding software is developed with the knowledge embedded. The predicted phase stabilities and elastic constants of the *FCC and BCC binary systems* are shown below: (a)  $\Delta H^{f}$ of FCC; (b) $\Delta H^{f}$ of BCC; (c) $C_{ij}$ of FCC; and (d) $C_{ij}$ of BCC.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.3_Binary.jpg' alt='' width='700'/></div>

* The VEC is defined as follows: \
$VEC=\sum C_ {i}(VEC)_ {i}$, \
where $C_ {i}$ and $(VEC)_ {i}$ stand for the atomic fraction and VEC value of element $i$, respectively. The corresponding VEC values of each element are listed in the table below.
    | Element | VEC |
    | :--- | :--- |
    | Al | 3 |
    | Co | 9 |
    | Cr | 6 |
    | Fe | 8 |
    | Ni | 10 |
* Prediction results in terms of the *VEC (see the definition above)* for FCC (a1-a8) and BCC (b1-b8): (a1/b1) $\Delta H^{f}$; (a2/b2) Bulk modulus; (a3/b3) Shear modulus; (a4/b4) Young’s modulus; (a5/b5) P-wave modulus; (a6/b6) Pugh’s ratio; (a7/b7) Poisson's ratio; and (a8/b8) Vickers hardness.

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.4_VEC.jpg' alt='' width='700'/></div>

### Analysis & Screening
* Analysis with an emphasis on bulk modulus (*B*), shear modulus (*G*), and Pugh’s ratio (*k*) with an elemental concentration of each range from 5 to 35 at. %: Univariate and bivariate distribution plots for the (a) FCC and (b) BCC. Mechanical properties vs. phase stabilities plots of the (c) FCC and (d) BCC

    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.5_Analysis.jpg' alt='' width='700'/></div>

* 100 candidates with the highest bulk modulus after screening for both (a) FCC and (b) BCC, sorted by phase stabilities. Screening criteria: (1) the concentration of each element in the range of 5 to 35 at. %; and (2) $\Delta H^{f}$ less than or equal to zero.
    
    <div align=left><img src='https://raw.githubusercontent.com/aguang5241/HEA_ML/main/res/Fig.6_Screening.jpg' alt='' width='700'/></div>


## References
1. G. Liu, S. Yang, Y. Zhong. High-entropy materials design by integrating the first-principles calculations and machine learning: a case study in the Al-Co-Cr-Fe-Ni system. (2022, in preparation, **this work**)
2. S. Yang, Y. Zhong, Ab Initio Modeling of fcc Fe-Co-Cr-Ni High Entropy Alloys with Full Composition Range, Journal of Phase Equilibria and Diffusion 42(5) (2021) 656-672.
3. S. Yang, G. Liu, Y. Zhong, Revisit the VEC criterion in high entropy alloys (HEAs) with high-throughput ab initio calculations: A case study with Al-Co-Cr-Fe-Ni system, Journal of Alloys and Compounds  (2022) 165477.
