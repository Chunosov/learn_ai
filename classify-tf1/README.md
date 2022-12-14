# Image classification example

An example for older TensorFlow 1.14.

## Prepare models

Download model and labels if they are not already downloaded:

```bash
../models/inception_v3/get.sh
```

## Prepare env

[Prepare Python 2.7 environment](../README.md#prepare-python-2-7). TF 1.* doesn't support Python 3.

This way works in Ubuntu 20.04, but does not in 22.04. There are tons or errors when installing TF 1.14, probably because of too new GCC or something. Use the docker approach there (see below).

```bash
# This is CPU-only version
pip install tensorflow=1.14.0

# Or install with GPU-support
# This requires both CUDA Toolkit 10.0 and cuDNN 7 to be installed
pip install tensorflow-gpu=1.14.0
```

Run the example

```bash
python main.py ../samples/docbrown.jpg
```

Run the benchmark example

```bash
python main.py --loops=10 ../samples/imagenet
```

## Run with GPU acceleration in docker

This approach uses a docker image already containig both CUDA Toolkit and cuDNN libraries.

```bash
../gpu-node/run10.sh build

# in the container
cd classify-ft1
python main.py ../samples/docbrown.jpg
python main.py --loops=10 ../samples/imagenet
```

## Compare GPU vs CPU

(remove `--device` propagation from `../gpu-node/run10.sh` to switch TF to CPU-only mode)

See in the [TF2 section](../classify-tf/README.md#compare-gpu-vs-cpu)
