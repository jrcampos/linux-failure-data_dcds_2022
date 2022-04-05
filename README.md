# A Dataset of Linux Failure Data for Dependability Evaluation and Improvement

This repository makes available a comprehensive failure dataset of Linux obtained through fault injection. Further details can be found in the paper **A Dataset of Linux Failure Data for Dependability Evaluation and Improvement** (currently under revision).

Besides the raw data, this repository also provides the full list of failure detectors and system metrics collected throughout the experiments. Be aware that not every experiment will have all the metrics, which can be due to either the injected faults or transient processes. These details can be found in the [appendix](./appendix.pdf).

Due to its size, the data is currently hosted [here](https://deiucpt-my.sharepoint.com/:f:/g/personal/jrcampos_dei_uc_pt/EpiYpLzRsG9MlxzGHyh9kt4BtwPXRsEA2YMNlGUHiTbmWQ?e=vLEstb).

Each experiment has the following structure:

- **logs**
  - *final_log.txt* - final complete log of all the relevant events and details of the experiment
  - *fsck_read.txt* - output of fsck functionality
  - *log.txt* - log of the experimental process
  - *vm.log_read.txt* - output of the tty of the VM
  - *mv.log_send.txt* - commands sent to the VM
  - *wkl.monitor.log.txt* - monitor of the workload process throughout the experiments
- **shared**
  - **log** - system logs from the VM (redirected)
    - *auth.log*
    - *dmesg.log*
    - *kern.log*
    - *mail.err*
    - *mail.log*
    - *syslog*
  - *mon.netdata.log.zip* - system metrics throughout the experiments
  - *posthoc-log.zip* - log folder from the VM, for posthoc analysis (logs that have been redirected will only have data up to that point)
  - *trace-pipe.log.zip* - ftrace output (used to monitor fault activation); this may have been terminated after registering fault activation to avoid overloading
  - *watchdog.txt* - watchdog used to monitor the state of the VM

The experiments are divided based on their outcomes:

- **failure** - experiments that led to failure more than 15s after fault activation
- **failure-corrupted-netdata** - failures where the monitor/data was corrupted (e.g., invalid structure)
- **failure-invalid** - experiments where the first failure occurred too close to fault injection
- **failure-invalid-activation** - experiments where the first failure occurred too close to fault activation
- **failure-invalid-netdata** - failures where the monitor data is not sequential (e.g., missing timestamps for >2s)
- **failure-late** - experiments where the first failure occurred after the workload ended
- **failure-noactivation** - failures where it was not possible to register when the fault was activated
- **golden** - runs where no faults were injected, to serve as a baseline
- **non-failure** - experiments where no failure was detected
- **non-failure-invalid-netdata** - experiments where no failure was detected but the monitored data was incomplete
- **non-failure-noactivation** - no failure was detected but it was not possible to register fault activation (it may, in fact, not have been activated)

The dataset and the process used to generate it are both comprehensive and complex. Feel free to contact me if you have any questions: jrcampos@dei.uc.pt .
