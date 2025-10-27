# DNA3_XLNet Model Weights - iEnhancer-XLNet3D

This repository contains the pre-trained weights for the **DNA3_XLNet** model, which is a reconstructed version of **XLNet** optimized for DNA sequence encoding. These weights are part of the **iEnhancer-XLNet3D** model designed for DNA enhancer recognition and functional genomics tasks.

## Overview

The **DNA3_XLNet** model utilizes a **3-mer tokenization strategy** specifically designed for genomic sequence representation. By using **closed-set 3-mer embeddings**, this model significantly reduces parameter size while maintaining the ability to capture important local sequence patterns and long-range dependencies, making it ideal for DNA sequence analysis, particularly for enhancer prediction tasks.

The pre-trained **DNA3_XLNet** weights in this repository are designed to be used in the **iEnhancer-XLNet3D** framework, which combines deep separable convolutions and a multi-layer feature fusion approach for enhanced DNA sequence modeling.

## Features

* **Optimized for DNA sequences** using a 3-mer tokenization strategy.
* **Pre-trained on genomic data** with a focus on enhancer recognition.
* **Efficient embedding** with a significant reduction in parameter size (approximately 99.8% smaller compared to the original XLNet).
* **Part of the iEnhancer-XLNet3D framework**, which includes full-layer fusion (FUSE-ENCODER) and depthwise separable convolutions (DDS_CNN).

## How to Use

### Requirements

* Python 3.6+
* PyTorch 1.7.0+

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/tilerons/iEnhancer-XLNet3D.git
   cd iEnhancer-XLNet3D
   ```

2. Install the required dependencies:

   ```bash
   pip install -r requirements.txt
   ```

3. Download the pre-trained model weights from the following Google Drive link:
   [Download DNA3_XLNet Weights](https://drive.google.com/drive/folders/18Y88_Rvu-qOSbP_8_HvUKFxIUqqwoAaq?usp=sharing)

4. Place the downloaded weights in the `models/` directory.

### Usage

Once you have the model weights and dependencies set up, you can load the pre-trained **DNA3_XLNet** model and use it for enhancer prediction as follows:

```python
from transformers import XLNetForSequenceClassification, XLNetTokenizer

# Load the pre-trained DNA3_XLNet model and tokenizer
model = XLNetForSequenceClassification.from_pretrained('path/to/downloaded/weights')
tokenizer = XLNetTokenizer.from_pretrained('path/to/downloaded/weights')

# Example DNA sequence
sequence = "ATGCATGCATGCATGC"

# Tokenize the sequence
inputs = tokenizer(sequence, return_tensors="pt")

# Get predictions
outputs = model(**inputs)
predictions = outputs.logits
```

### Fine-tuning

To fine-tune **DNA3_XLNet** on your own dataset for enhancer recognition, you can adapt the model by following the **iEnhancer-XLNet3D** framework's training pipeline. Instructions for fine-tuning can be found in the detailed documentation of the framework.
