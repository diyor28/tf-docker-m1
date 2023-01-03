# Deprecated
This repo is deprecated in favor of https://github.com/diyor28/tf-aarch64. [tf-aarch64](https://github.com/diyor28/tf-aarch64)
contains more wheels and more additional libraries.

# tf-docker-m1
Tensorflow and Tensorflow Addons prebuilt wheels for Linux running inside Docker container on Apple Silicon

### How to install

Make sure you have wheel installed
```shell
pip install wheel
```
Pick a tensorflow and python version from [here](https://github.com/diyor28/tf-docker-m1/releases/tag/v1.0.0)
and install using:
```shell
pip install https://github.com/diyor28/tf-docker-m1/releases/download/v1.0.0/tensorflow-2.8.0-cp39-cp39-linux_aarch64.whl
```

or in a `Dockerfile` using

```
RUN pip install https://github.com/diyor28/tf-docker-m1/releases/download/v1.0.0/tensorflow-2.8.0-cp39-cp39-linux_aarch64.whl
```

## Build from source
You can also build tensorflow from source for your platform using the `Dockerfile` included in the repository.
First clone the repository.
```shell
git clone https://github.com/diyor28/tf-docker-m1.git
```

Make sure to give your docker engine enough RAM since build may fail if the amount of RAM is insufficient.
Also give your docker engine as many cores as possible in Docker Desktop settings to make building faster.
On an 8-core (4 efficiency, 4 performance cores) M1 building takes about 5-8 hours.

Then run
```shell
cd tf-docker-m1/
docker build -t tensorflow:2.8 -f tensorflow/Dockerfile .
```

to build tensorflow-addons from source run
```shell
docker build -t tensorflow-addons:0.16 -f tensorflow-addons/Dockerfile .
```

### Supported versions

Python: 3.9, 3.8    
Tensorflow: 2.8  
Tensorflow-addons: 0.16 

NOTE: Other versions can be built and uploaded upon request.
