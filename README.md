# CO-DMO-CT (Co-optimization of DVS, Memory placement, and Offloading with compatible TEE)

This project implements real-time task scheduling using steady-state genetic algorithms to minimize power consumption in CPU, memory, and network subsystems while meeting deadline constraints.

CO-DMO-CT integrates three energy-saving techniques across different system layers:
- DVS (Dynamic Voltage Scaling): Adjusting voltage and frequency to reduce CPU power consumption.

- Persistent Memory Placement: Optimizing data placement to minimize memory energy usage.

- Task Offloading: Executing tasks on edge servers that support a Trusted Execution Environment (TEE) to ensure secure execution.

Two executables included in this project, which can simulate CO-DMO-CT in comparison with DVS, Offloading, and basic configurations.
- `gasgen`: task generation tool based on CPU and total utilization
- `gastask`: scheduling scheme generator based on GA

## Build
To build `gastask` and `gasgen`, use CMake:
```
$ mkdir -p build && cd build
$ cmake ..
$ make
$ cp gasgen gastask ../simulators/ 
```

## Run
- Create a new configuration file. Refer to `gastask.conf.tmpl`.
- run `gasgen`
```
# ./gasgen gastask.conf
```
- Tasks list will be generated into <code>task_generated.txt</code> <code>network_generated.txt</code> <code>network_commander_generated.txt</code>according to gastask.conf
- paste <code>task_generated.txt</code> into the task section of gastask.conf 
- paste <code>network_generated.txt</code> into the network section of gastask.conf
- paste <code>network_commander_generated.txt</code> into the net_commander_ section of gastask.conf
- run gastask
```
# ./gastask gastask.conf
```
- scheduling information is generated in <code>task.txt</code>.

## Batch run
- `run.sh` performs all procedures in batch
  - Before executing run.sh,  ./tmp folder should be generated in root.


## Data Set

There are two types of data set to perform the simulations of Co-TOMS.

- Synthetic workload: 
  - [20% CPU Utilization Workload](dataset/synthetic/cpu_20):
  - [30% CPU Utilization Workload](dataset/synthetic/cpu_30):
  - [40% CPU Utilization Workload](dataset/synthetic/cpu_40):
  - [50% CPU Utilization Workload](dataset/synthetic/cpu_50):
  - [60% CPU Utilization Workload](dataset/synthetic/cpu_60):
  - [70% CPU Utilization Workload](dataset/synthetic/cpu_70):
  - [80% CPU Utilization Workload](dataset/synthetic/cpu_80):
  - [90% CPU Utilization Workload](dataset/synthetic/cpu_90):

- Realistic worload:
  - [Robotic Highway Safety Marker (RSM)](dataset/realistic/RSM): real-time task set for the actions of mobile robots that carry safety markers in a highway for road construction safety
  - [IoT](dataset/realistic/IoT): real-time task set for the actions of a controller in industry machine hands
