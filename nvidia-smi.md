

```bash

$ nvidia-smi -h

NVIDIA System Management Interface -- v530.30.02
NVIDIA 系统管理界面 -- v530.30.02

NVSMI provides monitoring information for Tesla and select Quadro devices.
The data is presented in either a plain text or an XML format, via stdout or a file.
NVSMI also provides several management operations for changing the device state.
NVSMI 提供 Tesla 和部分 Quadro 设备的监控信息。
数据通过 stdout 或文件以纯文本或 XML 格式呈现。
NVSMI 还提供了多种用于更改设备状态的管理操作。

Note that the functionality of NVSMI is exposed through the NVML C-based
library. See the NVIDIA developer website for more information about NVML.
Python wrappers to NVML are also available. The output of NVSMI is
not guaranteed to be backwards compatible; NVML and the bindings are backwards
compatible.
请注意，NVSMI 的功能是通过基于 C 的 NVML 公开的
图书馆。 有关 NVML 的更多信息，请参阅 NVIDIA 开发人员网站。
NVML 的 Python 包装器也可用。 NVSMI 的输出是
不保证向后兼容； NVML 和绑定是向后的兼容的。

http://developer.nvidia.com/nvidia-management-library-nvml/
http://pypi.python.org/pypi/nvidia-ml-py/

Supported products:  支持的产品：
- Full Support  全力支持
    - All Tesla products, starting with the Kepler architecture  所有特斯拉产品，从开普勒架构开始
    - All Quadro products, starting with the Kepler architecture  所有 Quadro 产品，从 Kepler 架构开始
    - All GRID products, starting with the Kepler architecture  所有 GRID 产品，从 Kepler 架构开始
    - GeForce Titan products, starting with the Kepler architecture  GeForce Titan 产品，从 Kepler 架构开始
- Limited Support  有限的支持
    - All Geforce products, starting with the Kepler architecture  所有 Geforce 产品，从 Kepler 架构开始

################################################################################################################

nvidia-smi [OPTION1 [ARG1]] [OPTION2 [ARG2]] ...

    -h,   --help                Print usage information and exit.

################################################################################################################

  LIST OPTIONS:

    -L,   --list-gpus           Display a list of GPUs connected to the system.
    显示连接到系统的 GPU 列表。

[root@middle-wy-p13182 ~]# nvidia-smi -L
GPU 0: Tesla T4 (UUID: GPU-c1d02d08-2915-752a-ef58-a46a0718a45d)
[root@middle-wy-p13182 ~]#

################################################################################################################

    -B,   --list-excluded-gpus  Display a list of excluded GPUs in the system.
    显示系统中排除的 GPU 的列表。

[root@middle-wy-p13182 ~]# nvidia-smi -B
No excluded devices found.
[root@middle-wy-p13182 ~]#

################################################################################################################

  SUMMARY OPTIONS:

    <no arguments>              Show a summary of GPUs connected to the system.
    显示连接到系统的 GPU 的摘要。

    [plus any of]

    -i,   --id=                 Target a specific GPU.  定位特定 GPU。
    -f,   --filename=           Log to a specified file, rather than to stdout.  记录到指定的文件，而不是标准输出。
    -l,   --loop=               Probe until Ctrl+C at specified second interval.  以指定的第二个间隔进行探测，直到按 Ctrl+C。

[root@middle-wy-p13182 ~]# nvidia-smi
Wed Jul  5 20:05:11 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Tesla T4                        On | 00000000:00:08.0 Off |                    0 |
| N/A   38C    P8               11W /  70W|     31MiB / 15360MiB |      0%   E. Process |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A     25384      C   nvidia-cuda-mps-server                       26MiB |
+---------------------------------------------------------------------------------------+

nvidia-smi命令用于查看NVIDIA GPU的状态和信息。以下是nvidia-smi命令输出的一些常见字段及其含义：

1. Driver Version: 显示安装的NVIDIA驱动程序的版本号。

2. CUDA Version: 显示安装的CUDA工具包的版本号。

3. GPU Utilization: 显示GPU的利用率，包括图形运算和计算运算的百分比。

4. Memory Utilization: 显示GPU显存的利用率，以百分比表示。

5. Power Draw: 显示GPU的功耗，以瓦特（W）为单位。

6. Temperature: 显示GPU的温度，以摄氏度（℃）为单位。

7. Fan Speed: 显示GPU风扇的转速，以百分比表示。

8. Performance State: 显示GPU的性能状态，通常为一个编号，表示不同的性能级别。

9. ECC Mode: 显示GPU的纠错码（ECC）模式，指示是否启用了纠错功能。

10. Total Memory: 显示GPU的总显存大小，以字节为单位。

11. Used Memory: 显示当前正在使用的GPU显存大小，以字节为单位。

12. Processes: 显示当前在GPU上运行的进程和它们占用的显存大小。

[root@middle-wy-p13182 ~]#
[root@middle-wy-p13182 ~]# nvidia-smi -i 0
Wed Jul  5 20:05:17 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Tesla T4                        On | 00000000:00:08.0 Off |                    0 |
| N/A   38C    P8               11W /  70W|     31MiB / 15360MiB |      0%   E. Process |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A     25384      C   nvidia-cuda-mps-server                       26MiB |
+---------------------------------------------------------------------------------------+
[root@middle-wy-p13182 ~]# nvidia-smi -i 1
No devices were found
[root@middle-wy-p13182 ~]#
[root@middle-wy-p13182 ~]# nvidia-smi -i 0 -l 2
Wed Jul  5 20:05:35 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Tesla T4                        On | 00000000:00:08.0 Off |                    0 |
| N/A   38C    P8               11W /  70W|     31MiB / 15360MiB |      0%   E. Process |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A     25384      C   nvidia-cuda-mps-server                       26MiB |
+---------------------------------------------------------------------------------------+
Wed Jul  5 20:05:37 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Tesla T4                        On | 00000000:00:08.0 Off |                    0 |
| N/A   37C    P8               11W /  70W|     31MiB / 15360MiB |      0%   E. Process |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A     25384      C   nvidia-cuda-mps-server                       26MiB |
+---------------------------------------------------------------------------------------+
Wed Jul  5 20:05:39 2023
+---------------------------------------------------------------------------------------+
| NVIDIA-SMI 530.30.02              Driver Version: 530.30.02    CUDA Version: 12.1     |
|-----------------------------------------+----------------------+----------------------+
| GPU  Name                  Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf            Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                                         |                      |               MIG M. |
|=========================================+======================+======================|
|   0  Tesla T4                        On | 00000000:00:08.0 Off |                    0 |
| N/A   37C    P8               11W /  70W|     31MiB / 15360MiB |      0%   E. Process |
|                                         |                      |                  N/A |
+-----------------------------------------+----------------------+----------------------+

+---------------------------------------------------------------------------------------+
| Processes:                                                                            |
|  GPU   GI   CI        PID   Type   Process name                            GPU Memory |
|        ID   ID                                                             Usage      |
|=======================================================================================|
|    0   N/A  N/A     25384      C   nvidia-cuda-mps-server                       26MiB |
+---------------------------------------------------------------------------------------+
^C[root@middle-wy-p13182 ~]#

################################################################################################################

  QUERY OPTIONS:

    -q,   --query               Display GPU or Unit info.

    [plus any of]

    -u,   --unit                Show unit, rather than GPU, attributes. 显示单元属性，而不是 GPU 属性。
    -i,   --id=                 Target a specific GPU or Unit.
    -f,   --filename=           Log to a specified file, rather than to stdout.
    -x,   --xml-format          Produce XML output.
          --dtd                 When showing xml output, embed DTD.
    -d,   --display=            Display only selected information: MEMORY,
                                    UTILIZATION, ECC, TEMPERATURE, POWER, CLOCK,
                                    COMPUTE, PIDS, PERFORMANCE, SUPPORTED_CLOCKS,
                                    PAGE_RETIREMENT, ACCOUNTING, ENCODER_STATS,
                                    SUPPORTED_GPU_TARGET_TEMP, VOLTAGE
                                    FBC_STATS, ROW_REMAPPER, RESET_STATUS
                                Flags can be combined with comma e.g. ECC,POWER.
                                Sampling data with max/min/avg is also returned
                                for POWER, UTILIZATION and CLOCK display types.
                                Doesn't work with -u or -x flags.
                                仅显示选定的信息：内存、
                                     利用率、ECC、温度、功率、时钟、
                                     计算、PIDS、性能、SUPPORTED_CLOCKS、
                                     页面_退休、会计、编码器_统计、
                                     SUPPORTED_GPU_TARGET_TEMP、电压
                                     FBC_STATS、ROW_REMAPPER、RESET_STATUS
                                 标志可以与逗号组合，例如 ECC、电源。
                                 还返回具有最大/最小/平均值的采样数据
                                 适用于电源、利用率和时钟显示类型。
                                 不适用于 -u 或 -x 标志。

    -l,   --loop=               Probe until Ctrl+C at specified second interval.

    -lms, --loop-ms=            Probe until Ctrl+C at specified millisecond interval.

[root@middle-wy-p13182 ~]# nvidia-smi -q

==============NVSMI LOG==============

Timestamp                                 : Wed Jul  5 20:07:18 2023
Driver Version                            : 530.30.02
CUDA Version                              : 12.1

Attached GPUs                             : 1
GPU 00000000:00:08.0
    Product Name                          : Tesla T4
    Product Brand                         : NVIDIA
    Product Architecture                  : Turing
    Display Mode                          : Enabled
    Display Active                        : Disabled
    Persistence Mode                      : Enabled
    MIG Mode
        Current                           : N/A
        Pending                           : N/A
    Accounting Mode                       : Disabled
    Accounting Mode Buffer Size           : 4000
    Driver Model
        Current                           : N/A
        Pending                           : N/A
    Serial Number                         : 1323321061164
    GPU UUID                              : GPU-c1d02d08-2915-752a-ef58-a46a0718a45d
    Minor Number                          : 0
    VBIOS Version                         : 90.04.38.00.03
    MultiGPU Board                        : No
    Board ID                              : 0x8
    Board Part Number                     : 900-2G183-0000-001
    GPU Part Number                       : 1EB8-895-A1
    FRU Part Number                       : N/A
    Module ID                             : 1
    Inforom Version
        Image Version                     : G183.0200.00.02
        OEM Object                        : 1.1
        ECC Object                        : 5.0
        Power Management Object           : N/A
    GPU Operation Mode
        Current                           : N/A
        Pending                           : N/A
    GSP Firmware Version                  : 530.30.02
    GPU Virtualization Mode
        Virtualization Mode               : Pass-Through
        Host VGPU Mode                    : N/A
    GPU Reset Status
        Reset Required                    : No
        Drain and Reset Recommended       : N/A
    IBMNPU
        Relaxed Ordering Mode             : N/A
    PCI
        Bus                               : 0x00
        Device                            : 0x08
        Domain                            : 0x0000
        Device Id                         : 0x1EB810DE
        Bus Id                            : 00000000:00:08.0
        Sub System Id                     : 0x12A210DE
        GPU Link Info
            PCIe Generation
                Max                       : 3
                Current                   : 1
                Device Current            : 1
                Device Max                : 3
                Host Max                  : N/A
            Link Width
                Max                       : 16x
                Current                   : 16x
        Bridge Chip
            Type                          : N/A
            Firmware                      : N/A
        Replays Since Reset               : 0
        Replay Number Rollovers           : 0
        Tx Throughput                     : 0 KB/s
        Rx Throughput                     : 0 KB/s
        Atomic Caps Inbound               : N/A
        Atomic Caps Outbound              : N/A
    Fan Speed                             : N/A
    Performance State                     : P8
    Clocks Throttle Reasons
        Idle                              : Active
        Applications Clocks Setting       : Not Active
        SW Power Cap                      : Not Active
        HW Slowdown                       : Not Active
            HW Thermal Slowdown           : Not Active
            HW Power Brake Slowdown       : Not Active
        Sync Boost                        : Not Active
        SW Thermal Slowdown               : Not Active
        Display Clock Setting             : Not Active
    FB Memory Usage
        Total                             : 15360 MiB
        Reserved                          : 393 MiB
        Used                              : 31 MiB
        Free                              : 14935 MiB
    BAR1 Memory Usage
        Total                             : 256 MiB
        Used                              : 5 MiB
        Free                              : 251 MiB
    Compute Mode                          : Exclusive_Process
    Utilization
        Gpu                               : 0 %
        Memory                            : 0 %
        Encoder                           : 0 %
        Decoder                           : 0 %
    Encoder Stats
        Active Sessions                   : 0
        Average FPS                       : 0
        Average Latency                   : 0
    FBC Stats
        Active Sessions                   : 0
        Average FPS                       : 0
        Average Latency                   : 0
    ECC Mode
        Current                           : Enabled
        Pending                           : Enabled
    ECC Errors
        Volatile
            SRAM Correctable              : 0
            SRAM Uncorrectable            : 0
            DRAM Correctable              : 0
            DRAM Uncorrectable            : 0
        Aggregate
            SRAM Correctable              : 0
            SRAM Uncorrectable            : 0
            DRAM Correctable              : 0
            DRAM Uncorrectable            : 0
    Retired Pages
        Single Bit ECC                    : 0
        Double Bit ECC                    : 0
        Pending Page Blacklist            : No
    Remapped Rows                         : N/A
    Temperature
        GPU Current Temp                  : 38 C
        GPU Shutdown Temp                 : 96 C
        GPU Slowdown Temp                 : 93 C
        GPU Max Operating Temp            : 85 C
        GPU Target Temperature            : N/A
        Memory Current Temp               : N/A
        Memory Max Operating Temp         : N/A
    Power Readings
        Power Management                  : Supported
        Power Draw                        : 14.04 W
        Power Limit                       : 70.00 W
        Default Power Limit               : 70.00 W
        Enforced Power Limit              : 70.00 W
        Min Power Limit                   : 60.00 W
        Max Power Limit                   : 70.00 W
    Clocks
        Graphics                          : 300 MHz
        SM                                : 300 MHz
        Memory                            : 405 MHz
        Video                             : 540 MHz
    Applications Clocks
        Graphics                          : 585 MHz
        Memory                            : 5001 MHz
    Default Applications Clocks
        Graphics                          : 585 MHz
        Memory                            : 5001 MHz
    Deferred Clocks
        Memory                            : N/A
    Max Clocks
        Graphics                          : 1590 MHz
        SM                                : 1590 MHz
        Memory                            : 5001 MHz
        Video                             : 1470 MHz
    Max Customer Boost Clocks
        Graphics                          : 1590 MHz
    Clock Policy
        Auto Boost                        : N/A
        Auto Boost Default                : N/A
    Voltage
        Graphics                          : N/A
    Fabric
        State                             : N/A
        Status                            : N/A
    Processes
        GPU instance ID                   : N/A
        Compute instance ID               : N/A
        Process ID                        : 25384
            Type                          : C
            Name                          : nvidia-cuda-mps-server
            Used GPU Memory               : 26 MiB

[root@middle-wy-p13182 ~]#
[root@middle-wy-p13182 ~]# nvidia-smi -q -u

==============NVSMI LOG==============

Timestamp                                 : Wed Jul  5 20:15:20 2023
Driver Version                            : 530.30.02
CUDA Version                              : 12.1

HIC Info                                  : N/A
Attached Units                            : 0

[root@middle-wy-p13182 ~]#
[root@middle-wy-p13182 ~]# nvidia-smi -q -d MEMORY

==============NVSMI LOG==============

Timestamp                                 : Wed Jul  5 20:15:54 2023
Driver Version                            : 530.30.02
CUDA Version                              : 12.1

Attached GPUs                             : 1
GPU 00000000:00:08.0
    FB Memory Usage
        Total                             : 15360 MiB
        Reserved                          : 393 MiB
        Used                              : 31 MiB
        Free                              : 14935 MiB
    BAR1 Memory Usage
        Total                             : 256 MiB
        Used                              : 5 MiB
        Free                              : 251 MiB

[root@middle-wy-p13182 ~]#

################################################################################################################

  SELECTIVE QUERY OPTIONS:

    Allows the caller to pass an explicit list of properties to query.
    允许调用者传递要查询的显式属性列表。

    [one of]

    --query-gpu                 Information about GPU. 有关 GPU 的信息。
                                Call --help-query-gpu for more info.
    --query-supported-clocks    List of supported clocks. 支持的时钟列表。
                                Call --help-query-supported-clocks for more info.
    --query-compute-apps        List of currently active compute processes. 前活动计算进程的列表。
                                Call --help-query-compute-apps for more info.
    --query-accounted-apps      List of accounted compute processes. 已核算计算进程的列表。
                                Call --help-query-accounted-apps for more info.
    --query-retired-pages       List of device memory pages that have been retired. 已停用的设备内存页列表。
                                Call --help-query-retired-pages for more info.
    --query-remapped-rows       Information about remapped rows. 有关重新映射行的信息。
                                Call --help-query-remapped-rows for more info.

    [mandatory] 强制的

    --format=                   Comma separated list of format options:
                                  csv - comma separated values (MANDATORY)
                                  noheader - skip the first line with column headers
                                  nounits - don't print units for numerical
                                             values
                                逗号分隔的格式选项列表：
                                   csv - 逗号分隔值（强制）
                                   noheader - 跳过带有列标题的第一行
                                   nounits - 不打印数字单位
                                              价值观

    [plus any of]

    -i,   --id=                 Target a specific GPU or Unit.
    -f,   --filename=           Log to a specified file, rather than to stdout.
    -l,   --loop=               Probe until Ctrl+C at specified second interval.
    -lms, --loop-ms=            Probe until Ctrl+C at specified millisecond interval.

[root@middle-wy-p13182 ~]# nvidia-smi --query-gpu=index,name,memory.total,memory.used,fabric.state --format=csv
index, name, memory.total [MiB], memory.used [MiB], fabric.state
0, Tesla T4, 15360 MiB, 31 MiB, state  N/A
[root@middle-wy-p13182 ~]#
[root@middle-wy-p13182 ~]# nvidia-smi --help-query-gpu

################################################################################################################

  DEVICE MODIFICATION OPTIONS: 设备修改选项：

    [any one of]

    -pm,  --persistence-mode=   Set persistence mode: 0/DISABLED, 1/ENABLED

    -e,   --ecc-config=         Toggle ECC support: 0/DISABLED, 1/ENABLED

    -p,   --reset-ecc-errors=   Reset ECC error counts: 0/VOLATILE, 1/AGGREGATE

    -c,   --compute-mode=       Set MODE for compute applications:
                                0/DEFAULT, 1/EXCLUSIVE_THREAD (DEPRECATED),
                                2/PROHIBITED, 3/EXCLUSIVE_PROCESS

          --gom=                Set GPU Operation Mode:
                                    0/ALL_ON, 1/COMPUTE, 2/LOW_DP

    -r    --gpu-reset           Trigger reset of the GPU.
                                Can be used to reset the GPU HW state in situations
                                that would otherwise require a machine reboot.
                                Typically useful if a double bit ECC error has
                                occurred.
                                Reset operations are not guarenteed to work in
                                all cases and should be used with caution.

    -vm   --virt-mode=          Switch GPU Virtualization Mode:
                                Sets GPU virtualization mode to 3/VGPU or 4/VSGA
                                Virtualization mode of a GPU can only be set when
                                it is running on a hypervisor.

    -lgc  --lock-gpu-clocks=    Specifies <minGpuClock,maxGpuClock> clocks as a
                                    pair (e.g. 1500,1500) that defines the range
                                    of desired locked GPU clock speed in MHz.
                                    Setting this will supercede application clocks
                                    and take effect regardless if an app is running.
                                    Input can also be a singular desired clock value
                                    (e.g. <GpuClockValue>). Optionally, --mode can be
                                    specified to indicate a special mode.

    -m    --mode=               Specifies the mode for --locked-gpu-clocks.
                                    Valid modes: 0, 1    -rgc  --reset-gpu-clocks
                                Resets the Gpu clocks to the default values.

    -lmc  --lock-memory-clocks=  Specifies <minMemClock,maxMemClock> clocks as a
                                    pair (e.g. 5100,5100) that defines the range
                                    of desired locked Memory clock speed in MHz.
                                    Input can also be a singular desired clock value
                                    (e.g. <MemClockValue>).

    -rmc  --reset-memory-clocks
                                Resets the Memory clocks to the default values.

    -lmcd --lock-memory-clocks-deferred=
                                    Specifies memClock clock to lock. This limit is
                                    applied after GPU reset. Note that, this limit is
                                    persistence across system reboots.    -rmcd --reset-memory-clocks-deferred
                                Resets the deferred Memory clocks applied.

    -ac   --applications-clocks= Specifies <memory,graphics> clocks as a
                                    pair (e.g. 2000,800) that defines GPU's
                                    speed in MHz while running applications on a GPU.

    -rac  --reset-applications-clocks
                                Resets the applications clocks to the default values.

    -pl   --power-limit=        Specifies maximum power management limit in watts.

    -cc   --cuda-clocks=        Overrides or restores default CUDA clocks.
                                In override mode, GPU clocks higher frequencies when running CUDA applications.
                                Only on supported devices starting from the Volta series.
                                Requires administrator privileges.
                                0/RESTORE_DEFAULT, 1/OVERRIDE

    -am   --accounting-mode=    Enable or disable Accounting Mode: 0/DISABLED, 1/ENABLED

    -caa  --clear-accounted-apps
                                Clears all the accounted PIDs in the buffer.

          --auto-boost-default= Set the default auto boost policy to 0/DISABLED
                                or 1/ENABLED, enforcing the change only after the
                                last boost client has exited.

          --auto-boost-permission=
                                Allow non-admin/root control over auto boost mode:
                                0/UNRESTRICTED, 1/RESTRICTED

    -mig  --multi-instance-gpu= Enable or disable Multi Instance GPU: 0/DISABLED, 1/ENABLED
                                Requires root.

    -gtt  --gpu-target-temp=    Set GPU Target Temperature for a GPU in degree celsius.
                                Requires administrator privileges

   [plus optional]

    -i,   --id=                 Target a specific GPU.
    -eow, --error-on-warning    Return a non-zero error for warnings.

################################################################################################################

  UNIT MODIFICATION OPTIONS:

    -t,   --toggle-led=         Set Unit LED state: 0/GREEN, 1/AMBER

   [plus optional]

    -i,   --id=                 Target a specific Unit.

################################################################################################################

  SHOW DTD OPTIONS:

          --dtd                 Print device DTD and exit.

     [plus optional]

    -f,   --filename=           Log to a specified file, rather than to stdout.
    -u,   --unit                Show unit, rather than device, DTD.

    --debug=                    Log encrypted debug information to a specified file.

[root@middle-wy-p13182 ~]# nvidia-smi --dtd
<!-- nvsmi_device_v12.dtd -->
<!ELEMENT nvidia_smi_log        (timestamp, driver_version, cuda_version, vgpu_driver_capability*,
                                 attached_gpus, error_string?, gpu*)>

<!ELEMENT timestamp             (#PCDATA)>
<!ELEMENT driver_version        (#PCDATA)>
<!ELEMENT cuda_version          (#PCDATA)>
<!ELEMENT vgpu_driver_capability (heterogenous_multivGPU)>
<!ELEMENT heterogenous_multivGPU (#PCDATA)>

...
<!ELEMENT state                 (#PCDATA)>
<!ELEMENT status                (#PCDATA)>

[root@middle-wy-p13182 ~]#

################################################################################################################

 STATISTICS: (DEPRECATED)
    stats                       Displays device statistics. "nvidia-smi stats -h" for more information.
                                "nvidia-smi stats" is deprecated and will be removed in CUDA 12.1.
                                Consider using "nvidia-smi dmon" instead.

################################################################################################################

 Device Monitoring:
    dmon                        Displays device stats in scrolling format.
                                "nvidia-smi dmon -h" for more information.

    daemon                      Runs in background and monitor devices as a daemon process.
                                This is an experimental feature. Not supported on Windows baremetal
                                "nvidia-smi daemon -h" for more information.

    replay                      Used to replay/extract the persistent stats generated by daemon.
                                This is an experimental feature.
                                "nvidia-smi replay -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi dmon
# gpu    pwr  gtemp  mtemp     sm    mem    enc    dec   mclk   pclk
# Idx      W      C      C      %      %      %      %    MHz    MHz
    0     11     38      -     0      0      0      0    405    300
    0     12     38      -     0      0      0      0    405    300
    0     11     38      -     0      0      0      0    405    300
    0     11     38      -     0      0      0      0    405    300
    0     11     37      -     0      0      0      0    405    300
    0     11     38      -     0      0      0      0    405    300
    0     11     38      -     0      0      0      0    405    300
^C[root@middle-wy-p13182 ~]#

################################################################################################################

 Process Monitoring:
    pmon                        Displays process stats in scrolling format.
                                "nvidia-smi pmon -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi pmon
# gpu         pid  type    sm    mem    enc    dec    command
# Idx           #   C/G     %      %      %      %    name
    0      25384     C     -     -     -     -   nvidia-cuda-mps
    0      25384     C     -     -     -     -   nvidia-cuda-mps
    0      25384     C     -     -     -     -   nvidia-cuda-mps
    0      25384     C     -     -     -     -   nvidia-cuda-mps
^C

[root@middle-wy-p13182 ~]#

################################################################################################################

 TOPOLOGY:
    topo                        Displays device/system topology. "nvidia-smi topo -h" for more information.

################################################################################################################

 DRAIN STATES:
    drain                       Displays/modifies GPU drain states for power idling. "nvidia-smi drain -h" for more information.

################################################################################################################

 NVLINK:
    nvlink                      Displays device nvlink information. "nvidia-smi nvlink -h" for more information.

################################################################################################################

 CLOCKS:
    clocks                      Control and query clock information. "nvidia-smi clocks -h" for more information.

################################################################################################################

 ENCODER SESSIONS:
    encodersessions             Displays device encoder sessions information. "nvidia-smi encodersessions -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi encodersessions
# GPU Session    Process   Codec       H       V Average     Average
# Idx      Id         Id    Type     Res     Res     FPS Latency(us)
    0       -          -       -       -       -       -           -
    0       -          -       -       -       -       -           -
    0       -          -       -       -       -       -           -
    0       -          -       -       -       -       -           -
^C


[root@middle-wy-p13182 ~]#

################################################################################################################

 FBC SESSIONS:
    fbcsessions                 Displays device FBC sessions information. "nvidia-smi fbcsessions -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi fbcsessions
# GPU   Session   Process   Display   Session Diff. Map  Class. Map       Capture   Max H   Max V     H     V   Average       Average
# Idx        Id        Id   Ordinal      Type     State       State          Mode     Res     Res   Res   Res       FPS   Latency(us)
    0         -         -         -         -         -           -             -       -       -     -     -         -             -
    0         -         -         -         -         -           -             -       -       -     -     -         -             -
    0         -         -         -         -         -           -             -       -       -     -     -         -             -
^C[root@middle-wy-p13182 ~]#

################################################################################################################

 GRID vGPU:
    vgpu                        Displays vGPU information. "nvidia-smi vgpu -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi vgpu
No supported devices in vGPU mode
[root@middle-wy-p13182 ~]#

################################################################################################################

 MIG:
    mig                         Provides controls for MIG management. "nvidia-smi mig -h" for more information.

[root@middle-wy-p13182 ~]# nvidia-smi mig --list-gpu-instance-profiles
No MIG-enabled devices found.
[root@middle-wy-p13182 ~]#

################################################################################################################

 COMPUTE POLICY:
    compute-policy              Control and query compute policies. "nvidia-smi compute-policy -h" for more information.

################################################################################################################

 BOOST SLIDER:
    boost-slider                Control and query boost sliders. "nvidia-smi boost-slider -h" for more information.

################################################################################################################

 POWER HINT:    power-hint                  Estimates GPU power usage. "nvidia-smi power-hint -h" for more information.

################################################################################################################

 BASE CLOCKS:    base-clocks                 Query GPU base clocks. "nvidia-smi base-clocks -h" for more information.

################################################################################################################

 COUNTER COLLECTION UNIT:
    ccu                         Control and query counter collection unit. "nvidia-smi ccu -h" for more information.

################################################################################################################

Please see the nvidia-smi(1) manual page for more detailed information.
$

```

