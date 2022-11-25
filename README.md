# pytorch-fourier-features-networks

PyTorch implementation of Implicit Neural Representation for a single image with **Fourier Features Networks**

The architecture of the network in this code is different with paper version.

( I modified the network to improve the psnr value of the reconstructed image. Please refer to the detailed explanation about model architecture below. )

 - My review of this paper(in Korean) : [[논문리뷰]Fourier Features Let Networks](https://docs.google.com/document/d/e/2PACX-1vShqO1emAryxVLIk8n52S-Y8PhS4UpvvmsJv0k-KAoLyqYklWqe9co7pf36Y4QdFN11QoN6-yrev_tw/pub)

![image](https://user-images.githubusercontent.com/118791836/203972577-5252b515-2324-442e-8576-bd29ec2ed541.png)

### Model Architecture

 - **Model Architecture**

ReconNet has three conv blocks and the last conv block of which the number of out_features is three(RGB values).

||
|------|
|Conv block|
|Conv block|
|Conv block|
|Conv(mapping_size, 3, kernel_size = 1, padding = 0)|
|sigmoid|
||

 - **Conv block**

||
|------|
|conv2d(mapping_size, mapping_size, kernel_size = 1, padding = 0)|
|leakyReLU|
|BatchNorm2d(mapping_size)|
||


### Info of files

|file name|content|
|------|---|
|`fourier_features_networks_demo.ipynb`|Implementation of fourier-features-networks in PyTorch (The network consists of convolution blocks)|
|`fourier_features_networks_demo_lin_ver.ipynb`|The network composed with nn.Linear layers (I just changed the `fourier_features_networks_demo.ipynb`'s conv block to linear block)|
|`fourier_features_networks_gauss_scale_test`|This code includes the part that shows a generated image for each scale value and the part that shows the graph showing PSNR changes during epoch |

<hr>

### Reference

 - Paper : Fourier Features Let Networks Learn High Frequency Functions in Low Dimensional Domains ( [link](https://proceedings.neurips.cc/paper/2020/file/55053683268957697aa39fba6f231c68-Paper.pdf) )
 
 ( [Demo version](https://colab.research.google.com/github/tancik/fourier-feature-networks/blob/master/Demo.ipynb#scrollTo=OcJUfBV0dCww) of this paper in Colab )

### Dataset

 - Dataset : [DIV2K_valid_HR](https://data.vision.ee.ethz.ch/cvl/DIV2K/) (download [here](http://data.vision.ee.ethz.ch/cvl/DIV2K/DIV2K_valid_HR.zip))
 
