## Install nvidia driver on harvester cluster

Based on example from: https://gitlab.com/nvidia/container-images/driver/-/tree/main/sle15

Key change is swap out base image from sle bci to opensuse/leap

## Build image ##
```
docker build -t gmehta3/nvidia-sles:dev \
    --build-arg DRIVER_VERSION="510.85.02" \
    --build-arg CUDA_VERSION="11.7.1" \
    --build-arg SLES_VERSION="15.4" \
    ./sle15
```

push image to repo 

```
docker push gmehta3/nvidia-sles:dev
```

## deploy image

Based on deployment example from: https://github.com/NVIDIA/gpu-operator/tree/master/assets/state-driver

To deploy run the following against a target cluster:
```
kubectl apply -f ./deploy/
```