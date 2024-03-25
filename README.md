# Octo Experiments

This repository holds code for a GPU-powered dev container environment with the Octo model and some code to experiment around with the model.

## Setup

Enter VS Code and open this repository. Install the Dev Containers extension (and Docker + Nvidia Container Toolkit in case it is not installed). Then, simply open the workspace as dev container. 

Once setup has finished, you can test the installation by using the demo finetuning script from Octo. Be aware that in the beginning, some warnings are triggered from tensorflow - this seems to be ok, as tensorflow seems to be mainly used for data preprocessing and data loading using CPU operations.