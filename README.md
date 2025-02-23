## Project Overview 🔎

SymbioteNet is a mechanistic interpretebility network that helps in automatically mapping the primary model's circuitry. It does this by actively experimenting with "diffing" the primary models weights, and observing the subsequent behavioural changes. SymbioteNet is a secondary neural network that is iteratively trained to work alongside a primary model. Its main purpose is to selectively inhibit specific unwanted outputs from the primary model while preserving the model's performance on desired outputs. The system's effectiveness is evaluated under two conditions:
1. Normal operating conditions 
2. Polysemantic conditions 
<img width="1000" alt="SymbiotNet" src="https://github.com/user-attachments/assets/265d3a0e-183d-44da-8dd6-7522ef1a0f0e">
Weight inhibiting visualisation:

<img width="1000" alt="Weight inhibiting" src="https://github.com/user-attachments/assets/c7ec42b0-2bdf-4946-98c6-9bc75c84d15d">

### To get started:
1. Create a conda env:
```
conda env create -f environment.yml

```

2. Install lfs:
```
# For Mac (using Homebrew)
brew install git-lfs

# For Ubuntu/Debian
sudo apt install git-lfs

# For Windows (using Chocolatey)
choco install git-lfs

```

3. Pull the dataset:
```
git lfs install
git lfs pull
```

4. Run the notebook to witness the Symbiosis :)

### Process description:
In this project I train and test models on an MNIST dataset. The ground model A is a CNN that classifies digits 1-10 like in a traditional MNIST. I then train the  "Symbiote" model B (MLP) to adjust the activations of model A during infrerence according to what input I want it to inhibit in model A. To be exact, after training the model A, I train the "Symbiote" in a supervised fashion by providing it a single number from 1-10 which the model should discriminate by acting on model A's activations during inference such that it classifies all digits correctly, but never outputs the specified digit (i.e: if we input 1 into the Symbiote model, the output should always be 2-10, but not 1).

