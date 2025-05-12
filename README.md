# Sloth

This is the repository related to the Sloth paper. It contains dataset used to generate plots and Sloth's implementation 

## Datasets

Into the data folder, you'll find datasets used for the Sloth Paper :

* ***heatmap/*** : Contains a comparison of DPDK and Linux sockets. The DPDK points are used to draw a heatmap showing the energy efficiency of each freq/cores configuration
* ***runs-g5k/*** : Contains results of experiments on [Grid500](https://www.grid5000.fr), exploring many cpu/cores configurations at different throughput to measure their latencies and power consumption.
* ***training-trace/***: Contains results of experiments on our local setup, exploring many cpu/cores configurations at different throughput to measure their latencies and power consumption **using the caida trace**.
* **sloth-sota** : Dataset comparing Sloth to other state-of-the-art alternatives and DPDK Polling on our local setup

## fastlick-sloth

A first version of Sloth integrated within Fastclick is available under the `fastclick-sloth` repository.

### Building

You must follow these building steps

```bash
cd fastclick-sloth/
./configure.sh
make -j $(nproc)
```

### Setting up

An example config file is available under `fastclick-sloth/CONFIG`. In contains one line you should adjust in order to setup *fastclick-sloth* :

```fastclick
FromDPDKDevice(0, PRCTL 1, MAXTHREADS 12, VERBOSE 99, PROMISC true, PAUSE none, SLEEP_MODE sloth, SLEEP_DELTA 0, SLEEP_MAX 256, SUSPEND_THRESHOLD 256, NUMA_NODE 1, BURST 32, NDESC 4096, MINQUEUES 12,MIN_FREQUENCY 1000, MAXQUEUES 12,SLOTH_LAT 50, SLOTH_OPTIMUMS /etinfo/users2/delzotti/energy-aware-packet-scheduling/throughput_table_trace.csv, DUNEISH_CORE_THRESHOLD 230000, DUNEISH_FREQ_THRESHOLD 1000000, SLOTH_SCALE 5, SLOTH_PENALTY 0)
```

Importants parameters are :

- `PRCTL` (boolean, 1 or 0) : Tells wether you want to reduce the Linux SLACK_TIME to it's minimal 1ns value (1) or to it's default value (0)
- `SLEEP_MODE` (string) : Which execution do you want. Leave it to *sloth* to execute Sloth.
- `MINQUEUES/MAXQUEUES` : Sets maximum and minimal number of queues (and hence the number of available cores). Ideally both should be set to the same value.
- `SLOTH_LAT`(uint) : Latency objective Sloth should follow
- `SLOTH_OPTIMUMS` (string) : Path the the optimums table as a .csv format
- `SLOTH_PENALTY` (boolean, 1 or 0) : Indicates whether you want Sloth to perform online adjustment on your optimums table (1) or not (0).

### Running

Once build, fastclick can be run with :

```bash
sudo ./bin/click --dpdk -a your:pcie:address -l 0-MAXCORE -- CONFIG
```

## Sloth 

We are currently working on realising Sloth. Stay tuned !
