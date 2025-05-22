<!--
 * @Author: Guoxin Wang
 * @Date: 2024-02-07 07:47:56
 * @LastEditors: Guoxin Wang
 * @LastEditTime: 2024-02-07 12:11:35
 * @FilePath: /DeepECG/README.md
 * @Description: 
 * 
 * Copyright (c) 2024 by Guoxin Wang, All Rights Reserved. 
-->
# AuthECG

## Introduction

Build a deep neural network for ECG authentication

[Low Complexity ECG Biometric Authentication for IoT Edge Devices](https://ieeexplore.ieee.org/document/9332012)

The whole project contains three different methods to rebuild the model and execute ECG authentication:

- Original CNN

This rebuilds the model from a pre-trained CNN model and uses its **original weights**. The best performance is **99.63%**.

- Binary Neural Network

This rebuilds the model from a pre-trained CNN model and uses **binary weights**. The weights are in this format:

$$\pm1$$

The best performance is **88.85%**

- Exponentiation Neural Network

This rebuilds the model from a pre-trained CNN model and uses **exponential weights**. The weights are in this format:

$$\frac{INTEGER}{2^n}$$

**The performance increases with a larger 'n' value**

## Requirements and Installation

- Database

[PTB Diagnostic ECG Database](https://physionet.org/content/ptbdb/1.0.0/)

- Libraries

Install the necessary libraries:

```cmd
conda env create --file environment.yml
```

Activate environment:

```cmd
conda activate authecg
```

## Usage

- Step 1: Data Processing

To process data from the original dataset manually, run the following:

```cmd
python DataGeneration.py \
    --data_path ${data_path} \
    --prefix ${prefix} \
    --output_path ${output_path}
```

Or you can download the pre-processed dataset from the link:

[PTB Processed Dataset](https://huggingface.co/datasets/PriceWang/dataset/resolve/main/deepecg/ptbdb_prt.csv)

- Step 2: CNN Modelling

To build the CNN model for human recognition, run:

```cmd
python ModelCreation.py \
    --save_path ${save_path} \
    --data_path ${data_path}
```

- Step 3: Authentication

To execute the authentication section, run the following:

```cmd
python Authentication.py \
    --model_path ${model_path} \
    --data_path ${data_path}
```

## Update

- 2021/01/20

optimize structure, improve performance, test generalization ability

- 2021/02/05

optimize path search

- 2021/03/16 *

update path structure

- 2021/05/10

pruning
