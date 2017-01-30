#Deep learning environment setup metaguide

Props to @[anujonthemove](https://github.com/anujonthemove) for helping me out when I
was having trouble, I hope this document helps you as much.

I encourage you to fork this repo and make your own additions.

Below are notes and links to resources for setting up a deep learning
environment on a PC/laptop with an NVIDIA GPU. This includes the following (in
the order of installation):

- NVIDIA drivers
- CUDA
- Anaconda scientific Python distribution (highly recommended, but optional)
- theano
- keras
- cuDNN

These are not detailed instructions as I link to posts
that are more comprehensive than I can hope to be. 
I'm certain that anyone who tries to retrace the steps posted in this (or any)
guide are bound to run into different issues, it is my hope that the
information contained herein should be adequate to solve your problems, at the
very least cover common issues.
The hardware I installed this on was laptop with an Intel i5 processor and 
mobile GTX960 NVIDIA GPU, in general it's easier to install on a desktop.

##Prerequisite:

- Ubuntu 14.04 LTS(Long Term Support)- This is a solid, stable version of ubuntu
and supported until 2019. You could try the more recent 16.04 LTS but it's
still relatively new, unstable and I found it harder to find resources on how
to fix issues that I ran into. I ended up downgrading to 14.04 and installation
became far easier 
- NVIDIA GPU 

##Notes:

- IMO, getting the NVIDIA drivers to work are the hard part, the rest of them
  are are a breeze. CUDA and cuDNN just require downloading packages, copying
  them to specific locations on your drive and adding a few lines to your
  bashrc. 

- There are two ways to install the NVIDIA drivers, either through the
  [graphics-drivers ppa](https://webup8.org/2016/06/how-to-install-latest-nvidia-drivers-in.html)
  and apt-get or by using the [official linux installer](https://gist.github.com/wangruohui/df039f0dc434d6486f5d4d098aa52d07) 
  While the latter means getting the latest version, the ppa method was the one
  that did it for me. (Version 375)

- If you have a relatively new computer, you probably have UEFI. You need to
  disable  secure boot in that case by going to the bios. Look up the
  instructions for your PC

- If you face a login loop
    - <https://linuxslaves.com/2016/05/3-ways-fix-ubuntu-gets-stuck-login-loop.html>
    - This didn't help me fix it :P but it might help you

- To check if the driver successfully installed, use the nvidia-smi tool to
  check current cpu temperature. Then run glxgears (part of mesa-utils) to see
  if it heats up. The drivers should also install the nvidia xserver settings
  app that lets you check useful info about the GPU, switch between internal
  graphic and the GPU, etc.

- Use this **ONLY** for installing CUDA (and maybe cuDNN) not for the Nvidia
  drivers
    - <https://pyimagesearch.com/2016/07/04/how-to-install-cuda-toolkit-and-cudnn-for-deep-learning/>
    - You can use a newer version of CUDA if you want. At the time of writing,
      the latest is version 8.0.44

- Once the NVIDIA drivers and CUDA are installed, use [this](https://github.com/fastai/courses/blob/master/setup/install-gpu.sh) script from the MOOC @ course.fast.ai) and continue running
  it from line 14 (If you plan to use Anaconda)

- Python packages are even easier to install if you use the Anaconda Python
  distribution.  Anaconda is a distribution of Python with the most common
  packages needed for scientific computing (think numpy, matplotlib,
  scikit-learn) and comes bundled with a powerful package manager 'conda'.
  Using it means you don't need to compile the larger libraries and you'll stay
  up to date with the latest releases of most packages (packages downloaded via
  pip are generally a few versions out of date)

###Full installation instructions 
I haven't used these, you might get some mileage from them

- <https://github.com/saiprashanths/dl-setup#basics>
- Below is a docker image that runs on the GPU, should simplify and
standardize the installation of CUDA, cuDNN but it's my opinion that those are
the easy parts, they still require manual installation of NVIDIA drivers.
    - <https://github.com/NVIDIA/nvidia-docker>
