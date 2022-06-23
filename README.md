# NCU-VMDataset
Experimental data: Average virtual machine (VM) boot time (in seconds) on the host. Each average VM boot time is the average of at least 5 records.

- Experiment VM (eVM): The eVM is a VM used to measure the boot time, and will not execute any load after booting.
- Workload VM (wVM): The wVM is a VM that runs Stress to simulate a running VM and will compete for computing resources, especially CPU resources.

## Description of each page in the file (VM boot time for 4 computing hosts.xlsx):
  - dataset: This dataset includes the average VM boot time of host i in two experiments and is used to train and test machine learning-based models. The first experiment has 312 test cases, and the second experiment has 7200 test cases, and 18 test cases in the two experiments are the same.
    - First experiment: The average VM boot time of a host (Compute 1, Compute 2, Compute 3, or Compute 4) when there are 1 to 6 eVMs and 0 to 12 wVMs on the host.
    - Second experiment: The average VM boot time of a hosts (Compute 1, Compute 2, or Compute 3) when there are 0 to 6 eVMs on each host (Compute 1, Compute 2, Compute 3, and Compute 4). 
  - training dataset: This dataset contains 75% of the above dataset, which is obtained using the "train_test_split" function of the "sklearn" library in Python.
  - test dataset: This dataset contains 25% of the fist dataset, which is obtained using the "train_test_split" function of the "sklearn" library in Python.
  - evaluation dataset (single-host): This dataset contains the average VM boot time of Compute 4 when there are 1 to 6 eVMs and 0 to 12 wVMs on Compute 4. It contains 78 cases.
  - evaluation dataset (multi-host): This dataset contains the average VM boot time of Compute 4 when there are 0 to 6 eVMs on each host (Compute 1, Compute 2, and Compute 3) and 1 to 6 eVMs on Compute 4. It contains 2058 cases.
  - C5 with 1G (single-host): The average VM boot time of Compute 5 with 1G network when there are 1 to 6 eVMs and 0 to 12 wVMs on Compute 4. It contains 78 cases.
  - 10G network (single-host): The average VM boot time of Compute 1, 2, 3, and 5 with 10G network when there are 1 to 6 eVMs and 0 to 12 wVMs on Compute 4. It contains 312 cases.

## Description of each page in the file (VM boot time for 7 computing hosts.xlsx):
  - original dataset: This dataset consists of two parts: (i) single-host: the average VM boot time per host when there are 1 to 6 eVMs and 0 to 12 wVMs on the host, and (ii) multi-host: the average VM boot time per host when there are 0 to 6 eVMs per host. The single-host part has 78 cases per host, and the multi-host part has 823542 cases per host. Due to the large number of cases in the multi-host part, we only measure 1% (the 8235 cases) of them to build the dataset. Furthermore, we remove the average VM boot time of Compute 4 from the multi-host part and use these removed data for the "evaluation dataset (multi-host)", which is described below. To sum up, the dataset has 49956 pieces of data which is consis of the single-host cases per host and 1% of all cases with 0 to 6 eVMs per host.
  - evaluation dataset (single-host): This dataset contains the average VM boot time of Compute 4 when there are 1 to 6 eVMs and 0 to 12 wVMs on Compute 4. It contains 78 cases.
  - evaluation dataset (multi-host): This dataset contains the average VM boot time of Compute 4 in the cases shown in the original dataset. It has 7066 cases because in some cases there is no VM on Compute 4.
  - 
## Description of each column in the file (VM boot ime.xlsx):
  - host: The name of host i. (C1 stands for Compute 1)
  - core: The number of CPU cores available on host i.
  - alpha: The I/O time spent in the boot process of an eVM when there is no resource contention on the selected host (host i).
  - beta: The CPU time spent in the boot process of an eVM on host i without resource contention.
  - evm: The number of eVMs on host i.
  - wvm: The number of wVMs on host i.
  - ovm: The sum of the minimum values of R<sub>j</sub> and c<sub>j, CPU</sub>-1 for all other hosts j.
  - ovm': The sum of the maximum values of 0 and R<sub>j</sub>-c<sub>j, CPU</sub>+1 for all other hosts j.
  - C{k}_e: The number of eVMs on host k in this case.
  - boot_time: Average VM boot time on host i.
