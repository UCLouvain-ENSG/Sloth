# Sloth

This is the repository related to the Sloth paper. It contains dataset used to generate plots and Sloth's implementation 

## Datasets

Into the data folder, you'll find datasets used for the Sloth Paper :

* ***heatmap/*** : Contains a comparison of DPDK and Linux sockets. The DPDK points are used to draw a heatmap showing the energy efficiency of each freq/cores configuration
* ***runs-g5k/*** : Contains results of experiments on [Grid500](https://www.grid5000.fr), exploring many cpu/cores configurations at different throughput to measure their latencies and power consumption.
* ***training-trace/***: Contains results of experiments on our local setup, exploring many cpu/cores configurations at different throughput to measure their latencies and power consumption **using the caida trace**.
* **sloth-sota** : Dataset comparing Sloth to other state-of-the-art alternatives and DPDK Polling on our local setup


## Sloth 

We are currently working on realising Sloth. Stay tuned !
