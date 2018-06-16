# DCGAN-Pytorch

A pytorch implementation of [Unsupervised Representation Learning with Deep Convolutional Generative Adversarial Networks](https://arxiv.org/abs/1511.06434)

### Project structure:
```
├── agents
|  └── dcgan.py # the main training agent for the dcgan
├── graphs
|  └── models
|  |  └── discriminator.py  # discriminator model definition
|  |  └── generator.py  # generator model definition
|  └── losses
|  |  └── loss.py # contains the binary cross entropy 
├── datasets  # contains all dataloaders for the project
|  └── celebA.py # dataloader for celebA dataset
├── data
|  └── celebA  # contains all celebA images
├── utils # utilities folder containing metrics , config parsing, etc
├── main.py
├── run.sh
```

### Data Preparation:
CelebA dataset has been used. Images are resized to 64x64. Data are placed into data/ folder.

### Model:
![alt text](https://github.com/hagerrady13/DCGAN-Pytorch/blob/master/figures/gan_arch.png "Generator")
However, the number of filters in our implementation goes from 512 -> 256 -> 128 -> 64. This can be tuned in the configurations file be editing the variables: num_filt_g and num_filt_d.
### Experiment configs:
```
- Input size: 64x64x3
- Batch size: 64
- Learning rate: 0.0002
- Betas for Adam: 0.5 and 0.999
- Number of epochs: 30
- Noise vector size: 100
- Starting number of generator filters: 64
- Starting number of discriminator filters: 64
```
### Usage:
- To run the project, you need to add your configurations into the folder configs/. An example of the configurations that should be passed can be found [here](https://github.com/hagerrady13/DCGAN-Pytorch/blob/master/configs/dcgan_exp.json)
- ``` sh run.sh ```
- To run on a GPU, you need to enable cuda in the config file.

### Results:
Loss: 
![alt text](https://github.com/hagerrady13/DCGAN-Pytorch/blob/master/figures/loss.png "Loss during training")

Generated Images after training:
![alt text](https://github.com/hagerrady13/DCGAN-Pytorch/blob/master/figures/samples_epoch_63320.png "Generated Images")

### Requirements:
- Pytorch: 0.3.1
- torchvision: 0.2.0
- tensorboardX: 1.1


### References:
- Pytorch official example: https://github.com/pytorch/examples/tree/master/dcgan
- DCGAN in torch: https://github.com/soumith/dcgan.torch
