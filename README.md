# tf-docker-m1
Tensorflow prebuilt wheel for Linux running inside Docker container on Apple Silicon

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

You can also build tensorflow from source for your platform using the `Dockerfile` included in the repository.
First clone the repository.
```shell
git clone https://github.com/diyor28/tf-docker-m1.git
```

Then run
```shell
cd tf-docker-m1/
docker build -t tensorflow-image .
```

### Supported versions

Python: v3.9
Tensorflow: v2.8

NOTE: Other versions can be built and uploaded upon request.
