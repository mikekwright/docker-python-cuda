Docker - Python 3, NVIDIA and Cuda
===================================

This simple docker image is the basis for being able to use gpu based python solutions
(such as tensorflow) in an environment where the gpu may or may-not be available as well
as without the need to use `nvidia-docker`.   

## Components

There are a few pieces that are needed to make everything work as expected.   

1. The Nvidia driver, this allows the system to not required a seperate volume to be mounted
2. The CUDA and CUDNN installations
3. Python

Once these pieces are all in place installing a library such as tensorflow will work using

    pip install tensorflow-gpu

## Usage

If you wish to enable gpu support in the calls you will need to make sure the dev points are
added to the image when started (in privileged mode).  

    docker run --device /dev/nvidiactl --device /dev/nvidia-uvm --device /dev/nvidia{/d} mikewright/python-cuda

If you were to run without the devices, the libraries would all be there, but looking up devices
would fail.  

## References

So this image was created by referencing a number of other Dockerfile out there, so credit is
given where credit is due.  

[Source{d} install of nvidia driver (overall idea)](https://blog.sourced.tech/post/docker_coreos_gpu_deep_learning/)  
[NVIDIA CUDNN 5 Dockerfile](https://gitlab.com/nvidia/cuda/blob/ubuntu16.04/8.0/runtime/cudnn5/Dockerfile)  
[NVIDIA CUDA 8 Dockerfile](https://gitlab.com/nvidia/cuda/blob/ubuntu16.04/8.0/runtime/Dockerfile)  
[Python 3.6.1 Dockerfile](https://github.com/docker-library/python/blob/cd1f11aa745a05ddf6329678d5b12a097084681b/3.6/Dockerfile)   


