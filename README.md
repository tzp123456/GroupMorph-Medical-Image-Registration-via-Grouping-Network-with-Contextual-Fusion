# GroupMorph: Medical Image Registration via Grouping Network with Contextual Fusion
This is the official Pytorch implementation of "GroupMorph: Medical Image Registration via Grouping Network with Contextual Fusion".

Keywords: Deformable image registration, deformation decomposition, contextual feature fusion.
## Prerequisites
- `Python 3.8`
- `Pytorch 1.7.0`
- `NumPy`
- `NiBabel`
  
## Introduction
**Framework:**
![Framework](https://github.com/TVayne/GroupMorph/blob/main/figure/framwork.png)

**Decoder:**
![decoder](https://github.com/TVayne/GroupMorph/blob/main/figure/decoder.png)

We propose a novel registration model, called GroupMorph. Different from typical pyramid-based methods, we adopt the grouping-combination strategy to predict deformation field at each resolution. 
Specifically, we perform group-wise correlation calculation to measure the similarities of grouped features. After that, n groups of deformation subfields with different receptive fields are predicted in parallel. By composing these subfields, a deformation field with multi-receptive field ranges is formed, which can effectively identify both large and small deformations. Meanwhile, a contextual fusion module is designed to fuse the contextual features and provide the inter-group information for the field estimator of the next level. 
By leveraging the inter-group correspondence, the synergy among deformation subfields is enhanced.

## Training
After configuring the environment, please use this command to train the model.
```python
python train.py  --bs_ch=8  --dice=1 --smooth=0.5
```

## Testing
Use this command to obtain the testing results.
```python
python test.py --bs_ch=8 --modelpath=/xx/xx/
```
## Dataset
We used four datasets to validate our methods:

**OASIS:** We use the neuronal version, which undergoes preprocessing identical to that of [HyperMorph](https://arxiv.org/abs/2101.01035). The OASIS of neuronal version is available [here](https://github.com/adalca/medical-datasets/blob/master/neurite-oasis.md).

**IXI:** We use the IXI dataset that is preprocessed by [TransMorph](https://www.sciencedirect.com/science/article/abs/pii/S1361841522002432). Detailed introduction and download link can be found [here](https://github.com/junyuchen245/TransMorph_Transformer_for_Medical_Image_Registration/blob/main/IXI/TransMorph_on_IXI.md).

**Hippocampus Dataset:** The hippocampus dataset is available on [Learn2Reg Task 2](https://learn2reg.grand-challenge.org/Datasets/).

**Abdomen Dataset:** The abdomen dataset comes from Abdomen MR-CT Task in [Learn2Reg](https://learn2reg.grand-challenge.org/Datasets/) challenge.

## Acknowledgements
Some codes in this repository are modified from [LapIRN](https://github.com/cwmok/LapIRN) and [ULAE](https://github.com/wanghaostu/ULAE-net).

Thanks a lot for their great contribution!

