# Triton Go client

[Triton](https://github.com/triton-inference-server) ships a generated(based upon the [protobuf](https://developers.google.com/protocol-buffers) definitions), which can be found [here](https://github.com/triton-inference-server/client/tree/main/src/grpc_generated/go). It should be possible to also [generate a http client](https://developers.google.com/protocol-buffers/docs/reference/go-generated) based upon the proto definitions. 

In this case we will utilize the model developed in the previous blog post [Trition with post and pre processing](https://github.com/Njorda/trition-ensemble). 

Since the go grpc client is not exported and instead have to be generated, I have copied it inside here to make it easier. When trying to generate the client the code seems to be out of date and not working any longer but made a [PR](https://github.com/triton-inference-server/client/pull/138) that is not yet reviewed with suggested changes. For now I will assume we have it generated locally. 

Get the example image: 

```bash
    wget https://raw.githubusercontent.com/triton-inference-server/server/main/qa/images/mug.jpg -O "mug.jpg"
```


Th
```
go run main.go
```


This error seems to happen when you dont have enough memory for the automatic down cast to work:
```
[08/17/2022-06:53:37] [W] [TRT] parsers/onnx/onnx2trt_utils.cpp:368: Your ONNX model has been generated with INT64 weights, while TensorRT does not natively support INT64. Attempting to cast down to INT32.
```

Make sure your graphics card is not low on memory and ofc big enough for your model. 


```bash
    pip install numpy pillow torchvision opencv-python bson
```

```bash
apt-get update
apt-get install python3-opencv
```

to run the client
```
docker run --net=host -it -v $(pwd):/home gocv/opencv /bin/bash
```


https://github.com/triton-inference-server/server/blob/da3cc5b12055e737cfee53452a6edabfb25de49f/docs/model_configuration.md#datatypes

STRING

https://github.com/triton-inference-server/python_backend/blob/main/src/resources/triton_python_backend_utils.py


https://github.com/triton-inference-server/python_backend/blob/5b2c1a159b33f8dc17fb884df07aef82b622a3a0/examples/preprocessing/client.py#L92

https://github.com/triton-inference-server/client/blob/6cc412c50ca4282cec6e9f62b3c2781be433dcc6/src/python/library/tritonclient/grpc/__init__.py#L1795

