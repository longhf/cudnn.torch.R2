cudnn.torch
===========

Torch7 FFI bindings for NVidia CuDNN (R2) kernels!

Modules are API compatible their [`nn`](https://github.com/torch/nn) equivalents. Fully unit-tested against `nn` implementations.

#### Installation

* Install CuDNN (version R2)
* Have at least Cuda 6.5
* Have `libcudnn.so` in your library path (Install it from https://developer.nvidia.com/cuDNN )

#### Modules

```lua
-- All inputs have to be 3D or 4D(batch-mode), except ReLU, Tanh and Sigmoid
cudnn.SpatialConvolution(nInputPlane, nOutputPlane, kW, kH, [dW = 1], [dH = 1], [padW = 0], [padH = 0], [groups = 1])
cudnn.SpatialMaxPooling(kW, kH, dW, dH, padW, padH)
cudnn.SpatialAveragePooling(kW, kH, dW, dH, padW, padH)

-- the pointwise functions take an additional optional argument. if inplace=true then they do operations in-place without using any extra memory for themselves
cudnn.ReLU(inplace[=false])
cudnn.Tanh(inplace[=false])
cudnn.Sigmoid(inplace[=false])

-- SoftMax can be run in fast mode or accurate mode. Default is accurate mode.
cudnn.SoftMax(fastMode [= false])          -- SoftMax across each image (just like nn.SoftMax)
cudnn.SpatialSoftMax(fastMode [= false])   -- SoftMax across feature-maps (per spatial location)

-- Volumetric inputs (4D or 5D batched mode)
cudnn.VolumetricConvolution(nInputPlane, nOutputPlane, kT, kW, kH, dT, dW, dH, padT, padW, padH)
```

I have no time to support these, so please don't expect a quick response to filed github issues.

For version CuDNN R1, checkout the branch **R1**
