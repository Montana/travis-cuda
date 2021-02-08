# Travis CUDA test (NVIDIA's dev kit) build

[![Build Status](https://travis-ci.com/Montana/travis-cuda.svg?branch=master)](https://travis-ci.com/Montana/travis-cuda)

Test with Travis &amp; CUDA (NVIDIA's developer kit) 

## Getting started 

Make sure you have the `miniconda.sh` bash script, you could theoretically just run these as `script` hooks in Travis, but I recommend using the script: 

```bash
#!/bin/bash -x

# download and install
wget --quiet https://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh -O /tmp/miniconda.sh
bash /tmp/miniconda.sh -b -p $HOME/anaconda

export PATH=$HOME/anaconda/bin:$PATH # add to PATH
echo 'export PATH=$HOME/anaconda/bin:$PATH' >> ~/.bashrc # add to bashrc for future use
hash -r

# some configuration to make it easy to install things
conda config --set always_yes yes --set changeps1 no
conda update -q conda

# add channels to look for packages
conda config --add channels r # for backward compatibility with old r packages
conda config --add channels defaults
conda config --add channels conda-forge # additional common tools
conda config --add channels bioconda # useful bioinformatics

# display info
conda info -a

exit 0
```

Make sure you `chmod` in the `.travis.yml`
