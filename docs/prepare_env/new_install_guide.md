# Prepare the Environment
This guide is about building a python environment for Real3D-Portrait with Conda.

The following installation process is verified in ... + CUDA12.1.


# 1. Install CUDA
 We recommend to install CUDA `12.1` (which is verified in various types of GPUs), but other CUDA versions (such as `10.2`, `12.x`) may also work well. 

# 2. Install Python Packages
```
cd <Real3DPortraitRoot>
source <CondaRoot>/bin/activate
conda create -n real3dportrait python=3.12
conda activate real3dportrait
conda install conda-forge::ffmpeg # ffmpeg with libx264 codec to turn images to video

### We recommend torch2.3.1+cuda12.1. 
conda install pytorch==2.3.1 torchvision==0.18.1 torchaudio==2.3.1 -c pytorch -c nvidia 
# conda install pytorch-cuda=12.1 -c pytorch -c nvidia 

# Install from pytorch3d from conda (For fast installation, Linux only)
conda install pytorch3d::pytorch3d
## Alternatively, a choice of compatibility, build from Github's source code. 
## It may take a long time (maybe tens of minutes), Proxy is recommended if encountering the time-out problem
pip install "git+https://github.com/facebookresearch/pytorch3d.git@stable"

# MMCV for some network structure
pip install cython
pip install openmim==0.3.9
mim install mmcv==2.2.0 # use mim to speed up installation for mmcv


# prepare before install requirements.txt
git clone source code
check all module version (compatible with torch, python, cuda, scipy | frequently release new version)
install build-essential (included CMake)
install pk-config * OpenBLAS for ubuntu Version

# other dependencies
pip install -r docs/prepare_env/requirements.txt -v

If you encounter the following error, please try to install the dependencies with the following command:
pip install -r docs/prepare_env/requirements.txt -v --use-deprecated=legacy-resolver

> ERROR: pip's dependency resolver does not currently take into account all the packages
> that are installed. This behaviour is the source of the following dependency conflicts.
> openxlab 0.0.34 requires setuptools~=60.2.0, but you have setuptools 69.1.1 which is incompatible.

If pip cannot install any module, you can mannually install it later by conda
```
