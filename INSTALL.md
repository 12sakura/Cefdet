## Installation

**Requirements**

- Python
- Pytorch
- PyAV
- yacs
- OpenCV
- tensorboardX
- tqdm
- FFmpeg
- Cython
- Linux + Nvidia GPUs


We recommend to setup the environment with Anaconda, 
the step-by-step installation script is shown below.

```bash
conda create -n Cefdet python
conda activate Cefdet

# install pytorch with the same cuda version as in your environment
cuda_version=$(nvcc --version | grep -oP '(?<=release )[\d\.]*?(?=,)')
conda install pytorch torchvision cudatoolkit=$cuda_version -c pytorch

conda install av -c conda-forge
conda install cython

git clone https://github.com/12sakura/Cefdet.git
cd Cefdet
pip install -e .    # install other dependencies

```
### Errors frequently encountered + solutions

1. If the last command fails with `No CUDA found` error, it might be because Anaconda installed the CPU version of pytorch. Please use `pip install` with your prefered pytorch and cuda versions and try again. For instance, with torch 1.10.0 and cuda 10.2, you would run: `pip install torch==1.10.0+cu102 torchvision --extra-index-url https://download.pytorch.org/whl/cu102`

2. If the error is `fatal error: THC/THC.h: No such file or directory`, I suggest keep your pytorch version between 1.4.0 and 1.10.0, inclusive.

3. If you use a more recent GPU such as a `3080`, please try these commands to install `Cefdet`:
 ```
TORCH_CUDA_ARCH_LIST="8.0" python setup.py install
export TORCH_CUDA_ARCH_LIST=8.0
```
4. Any other issues? Please open an issue.

