High-level asks to make this work for VDIM
===========================================

* First step: make it work without triggering warnings. Currently there are warnings for pts_units for "pts" vs "sec". This needs to be addressed. Since we aren't using audio currently, perhaps we can just use "pts", but the warning needs to go away, and it needs to be verified that the videos coming out are correct (e.g., N frames at correct start / end points).

* Code is generally a mess and hard to debug. Comments and better documentation needs to be added to understand what the different variables are doing.

* The following functionality needs to be **verified** to reliably work with VideoClips (unit tests would be good):
  
  * The user needs to be able to simply specify whether to sample clips of length num_clips or length num_milliseconds or full video (3 options).
  
  * Dataset information needs to be more transparent. For instance, loading the data for the first time (for instance when computing clips) could be accompanied with information about the fps (consistent or consistent with exceptions or all different), video sizes (consistent or consistent with exceptions or all different), loading issues / errors with certain videos. Maybe mean and covariance of pixels and outlier pixel detection (I've done this with fMRI data and it can be useful).
  
* In addition, there are a bunch of TODO warnings in io/video.py. What are these doing and are they important? Does moving to dali make the actual loading easier? If so, maybe consider just going to dali for loading.

torchvision
===========

.. image:: https://travis-ci.org/pytorch/vision.svg?branch=master
    :target: https://travis-ci.org/pytorch/vision

.. image:: https://codecov.io/gh/pytorch/vision/branch/master/graph/badge.svg
    :target: https://codecov.io/gh/pytorch/vision

.. image:: https://pepy.tech/badge/torchvision
    :target: https://pepy.tech/project/torchvision

.. image:: https://img.shields.io/badge/dynamic/json.svg?label=docs&url=https%3A%2F%2Fpypi.org%2Fpypi%2Ftorchvision%2Fjson&query=%24.info.version&colorB=brightgreen&prefix=v
    :target: https://pytorch.org/docs/stable/torchvision/index.html


The torchvision package consists of popular datasets, model architectures, and common image transformations for computer vision.

Installation
============

TorchVision requires PyTorch 1.2 or newer.

Anaconda:

.. code:: bash

    conda install torchvision -c pytorch

pip:

.. code:: bash

    pip install torchvision

From source:

.. code:: bash

    python setup.py install
    # or, for OSX
    # MACOSX_DEPLOYMENT_TARGET=10.9 CC=clang CXX=clang++ python setup.py install

By default, GPU support is built if CUDA is found and ``torch.cuda.is_available()`` is true.
It's possible to force building GPU support by setting ``FORCE_CUDA=1`` environment variable,
which is useful when building a docker image.

Image Backend
=============
Torchvision currently supports the following image backends:

* `Pillow`_ (default)

* `Pillow-SIMD`_ - a **much faster** drop-in replacement for Pillow with SIMD. If installed will be used as the default.

* `accimage`_ - if installed can be activated by calling :code:`torchvision.set_image_backend('accimage')`

.. _Pillow : https://python-pillow.org/
.. _Pillow-SIMD : https://github.com/uploadcare/pillow-simd
.. _accimage: https://github.com/pytorch/accimage

C++ API
=======
TorchVision also offers a C++ API that contains C++ equivalent of python models. 

Installation From source:

.. code:: bash

    mkdir build
    cd build
    cmake ..
    make 
    make install

Documentation
=============
You can find the API documentation on the pytorch website: http://pytorch.org/docs/master/torchvision/

Contributing
============
We appreciate all contributions. If you are planning to contribute back bug-fixes, please do so without any further discussion. If you plan to contribute new features, utility functions or extensions, please first open an issue and discuss the feature with us.

Disclaimer on Datasets
======================

This is a utility library that downloads and prepares public datasets. We do not host or distribute these datasets, vouch for their quality or fairness, or claim that you have license to use the dataset. It is your responsibility to determine whether you have permission to use the dataset under the dataset's license.

If you're a dataset owner and wish to update any part of it (description, citation, etc.), or do not want your dataset to be included in this library, please get in touch through a GitHub issue. Thanks for your contribution to the ML community!
