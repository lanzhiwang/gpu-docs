## nvidia-docker

nvidia-docker 是一个用于在容器中使用 Nvidia GPU 的工具，它结合了 Docker 容器技术和 Nvidia GPU 驱动程序，使得在容器内部可以直接访问和利用宿主机上的 Nvidia GPU 资源。

传统的 Docker 平台默认不支持在容器内访问 GPU 资源，这限制了在容器中运行需要 GPU 加速的应用程序或任务。为了解决这个问题，Nvidia 开发了 nvidia-docker 工具，它提供了额外的功能和接口，以便在容器内部有效地使用 Nvidia GPU。

nvidia-docker 通过在容器内部安装 Nvidia GPU 驱动程序和 CUDA 工具包，并提供相应的容器运行时（container runtime）接口，使容器内的应用程序能够访问 GPU 设备和利用 CUDA 加速功能。它提供了一种简单且可重复的方法，让用户能够方便地将需要 GPU 加速的应用程序打包为 Docker 容器，并在支持 Nvidia GPU 的主机上运行。

使用 nvidia-docker，您可以轻松地在容器中运行深度学习任务、科学计算、图形渲染等需要 GPU 加速的应用程序，而无需手动配置 GPU 驱动程序和依赖项。

需要注意的是，nvidia-docker 只适用于支持 Nvidia GPU 的主机，并且需要在主机上正确安装 Nvidia GPU 驱动程序和 CUDA 工具包。同时，您需要安装适合您系统的 nvidia-docker 版本，并按照相关文档进行配置和使用。

请参考 Nvidia 官方的 nvidia-docker 文档和指南，以获取详细的安装、配置和使用说明。

https://github.com/NVIDIA/nvidia-docker

```bash
[root@middle-wy-p13182 ~]# cat /etc/docker/daemon.json
{
    "debug": false,
    "experimental": true,
    "insecure-registries": [
        "0.0.0.0/0"
    ],
    "ip-forward": true,
    "ipv6": false,
    "live-restore": true,
    "log-driver": "json-file",
    "log-level": "warn",
    "log-opts": {
        "max-file": "2",
        "max-size": "100m"
    },
    "runtimes": {
        "nvidia": {
            "args": [],
            "path": "nvidia-container-runtime"
        }
    },
    "selinux-enabled": false
}
[root@middle-wy-p13182 ~]#

[root@middle-wy-p13182 ~]# nvidia-ctk runtime help
NAME:
   NVIDIA Container Toolkit CLI runtime - A collection of runtime-related utilities for the NVIDIA Container Toolkit

USAGE:
   NVIDIA Container Toolkit CLI runtime [global options] command [command options] [arguments...]

COMMANDS:
   configure  Add a runtime to the specified container engine
   help, h    Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --help, -h  show help (default: false)
[root@middle-wy-p13182 ~]#

```

## nvidia-container-toolkit

nvidia-container-toolkit 是一个与 Docker 和 Kubernetes 集成的工具包，用于在容器化环境中管理和使用 Nvidia GPU 资源。它提供了一套工具和接口，以便在容器内部访问和利用宿主机上的 Nvidia GPU。

nvidia-container-toolkit 提供了以下主要功能：

1. GPU 设备插槽映射：通过 nvidia-container-runtime 接口，nvidia-container-toolkit 将宿主机上的 Nvidia GPU 设备映射到容器内部，使容器内的应用程序能够直接访问 GPU 设备。

2. CUDA 工具包支持：nvidia-container-toolkit 在容器内安装和配置了 Nvidia CUDA 工具包，使容器内的应用程序能够利用 CUDA 加速功能。

3. GPU 驱动程序兼容性：nvidia-container-toolkit 提供了容器内部 GPU 驱动程序和宿主机 GPU 驱动程序之间的兼容性，确保容器内的驱动程序与宿主机上的驱动程序版本匹配。

4. 运行时配置选项：nvidia-container-toolkit 允许您通过配置文件进行自定义设置，以调整 GPU 分配和使用的行为，如指定特定的 GPU 设备、GPU 内存限制等。

通过使用 nvidia-container-toolkit，您可以轻松地将需要 GPU 加速的应用程序打包为 Docker 镜像，并在支持 Nvidia GPU 的主机上运行这些镜像。它简化了在容器环境中使用 Nvidia GPU 的配置和管理，提供了一致和可靠的方法来利用 GPU 加速功能。

请注意，nvidia-container-toolkit 需要在支持 Nvidia GPU 的主机上正确安装 Nvidia GPU 驱动程序和 CUDA 工具包，并按照相关文档进行配置和使用。

请参考 Nvidia 官方的 nvidia-container-toolkit 文档和指南，以获取详细的安装、配置和使用说明。

https://github.com/NVIDIA/nvidia-container-toolkit

## nvidia-container-runtime

nvidia-container-runtime 是一个与容器运行时（container runtime）集成的组件，用于在容器环境中支持 Nvidia GPU 的运行。它是 Nvidia 提供的一个工具，与 Docker 和 Kubernetes 等常用的容器化平台集成，使得在容器内部能够正确访问和使用宿主机上的 Nvidia GPU 资源。

nvidia-container-runtime 提供了以下主要功能：

1. GPU 设备插槽映射：nvidia-container-runtime 通过与容器运行时的集成，将宿主机上的 Nvidia GPU 设备映射到容器内部，使容器内的应用程序能够直接访问 GPU 设备。

2. GPU 驱动程序和 CUDA 库的挂载：nvidia-container-runtime 允许在容器内部挂载宿主机上的 GPU 驱动程序和 CUDA 库，以便容器内的应用程序能够使用正确的驱动程序和 CUDA 功能。

3. 容器内 GPU 相关环境变量的设置：nvidia-container-runtime 在容器内设置必要的环境变量，以便应用程序能够正确识别和利用 GPU 资源，如设置 CUDA_VISIBLE_DEVICES 环境变量等。

通过使用 nvidia-container-runtime，您可以在容器内部运行需要 GPU 加速的应用程序，并确保这些应用程序能够正确地访问和使用宿主机上的 Nvidia GPU 资源。它与常见的容器化平台（如 Docker 和 Kubernetes）无缝集成，提供了一致和可靠的方法来利用 GPU 加速功能。

请注意，nvidia-container-runtime 需要与适当版本的 Nvidia GPU 驱动程序和 nvidia-container-toolkit 配合使用，以实现在容器内部正确访问和使用 Nvidia GPU 的功能。

请参考 Nvidia 官方的 nvidia-container-runtime 文档和指南，以获取详细的安装、配置和使用说明。

https://github.com/NVIDIA/nvidia-container-runtime

## 参考

[cuda](https://docs.nvidia.com/cuda/index.html)

可以使用 nvcc 命令查看 CUDA 版本信息。在终端中执行以下命令：
```bash
nvcc --version
```
如果命令输出显示 CUDA 版本信息，则表示 CUDA 已经安装。

[streams](https://docs.nvidia.com/cuda/cuda-c-programming-guide/index.html#streams)

[MPS](https://docs.nvidia.com/deploy/mps/index.html)

[time-slicing](https://docs.nvidia.com/datacenter/cloud-native/gpu-operator/latest/gpu-sharing.html)

[MIG](https://www.nvidia.com/en-us/technologies/multi-instance-gpu/)

[VGPU](https://docs.nvidia.com/grid/index.html)

[gpu-operator](https://docs.nvidia.com/datacenter/cloud-native/)

[NVIDIA GPU Architecture](https://www.nvidia.com/en-us/technologies/)





