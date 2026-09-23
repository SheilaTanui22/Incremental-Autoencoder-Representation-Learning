# Incremental Autoencoder Representation Learning

This repository contains the code and results from my research on developing an incremental autoencoder framework for data-driven architecture discovery and representation learning in fuzzy-encoded behavioral health data.

## Research Question

Instead of manually selecting the number of hidden layers and neurons in an autoencoder, can the architecture be grown incrementally based on reconstruction performance and internal representation diagnostics?

## Method

The autoencoder was constructed progressively. Neurons were added incrementally to each hidden layer, and the resulting representations were evaluated using reconstruction and structural diagnostics.

After selecting a layer, its representation was passed forward to construct the next layer.

The final discovered encoder architecture was:

129 → 100 → 71 → 58 → 48 → 37 → 34 → 24 → 18 → 14 → 13 → 12 → 7 → 7 → 6 → 5 → 4 → 4 → 4 → 3 → 2

This corresponds to 20 hidden layers and a final 2-dimensional latent representation.

## Evaluation

Model behavior was evaluated using:

- Reconstruction RMSE
- R² reconstruction performance
- Local and global reconstruction
- Validation and test performance
- Neuron redundancy
- Activation variance
- Neuron ablation
- Representation changes during incremental growth

Local reconstruction evaluates how well a newly added layer reconstructs the representation it receives.

Global reconstruction evaluates how much information from the original 129-dimensional input survives through the complete network.

## Incremental vs End-to-End Training

The architecture discovered through incremental training was subsequently trained jointly using end-to-end backpropagation.

This experiment investigates whether allowing gradients to propagate through the entire architecture can recover information that is lost when previously learned layers remain frozen.

For the 20-layer architecture:

| Training Strategy | Test R² |
|---|---:|
| Greedy incremental training | 0.0931 |
| End-to-end joint training | 0.1426 |

The end-to-end experiment therefore recovered part of the reconstruction performance lost through the deep frozen architecture, while the highly compressed 2-dimensional representation remained a major constraint.

## Next Steps

Ongoing analysis focuses on understanding:

- How representation quality changes with network depth
- Where information loss occurs in the frozen architecture
- How joint optimization reorganizes learned representations
- The trade-off between compression and reconstruction
- Whether the learned low-dimensional representations reveal meaningful structure in the behavioral health data

## Tools

MATLAB  
Deep Learning Toolbox  
Incremental Autoencoder Training  
Representation Learning  
Ablation Analysis

