FROM python:3.9.7 as tfa-build

RUN apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get -y install build-essential openjdk-11-jdk zip unzip wget
RUN wget https://github.com/bazelbuild/bazel/releases/download/4.2.1/bazel-4.2.1-dist.zip
RUN mkdir bazel-4.2.1mkdir bazel-4.2.1
RUN unzip -d ./bazel-4.2.1 bazel-4.2.1-dist.zip
WORKDIR /bazel-4.2.1
RUN env EXTRA_BAZEL_ARGS="--host_javabase=@local_jdk//:jdk" bash ./compile.sh
RUN cp output/bazel /usr/local/bin

WORKDIR /
RUN apt-get -y install git rsync
RUN pip install https://github.com/diyor28/tf-docker-m1/releases/download/v1.0.0/tensorflow-2.8.0-cp39-cp39-linux_aarch64.whl

RUN git clone https://github.com/tensorflow/addons.git
WORKDIR /addons
RUN git checkout r0.16
ENV TF_NEED_CUDA 0
RUN python ./configure.py
RUN bazel build build_pip_pkg
RUN bazel-bin/build_pip_pkg artifacts

FROM python:3.9.7 as tfa-install
RUN pip install https://github.com/diyor28/tf-docker-m1/releases/download/v1.0.0/tensorflow-2.8.0-cp39-cp39-linux_aarch64.whl
COPY --from=tfa-build /addons/artifacts/*.whl /wheels/
RUN pip install /wheels/tensorflow_addons-*.whl
RUN python -c "import tensorflow_addons as tfa"
CMD ["python"]
