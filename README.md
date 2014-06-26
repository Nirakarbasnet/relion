
RELION (REgularised LIkelihood OptimisatioN) playground
=======================================================
Run [RELION] at [NERSC]

Installation
------------
The installation is system-dependent
  
  - On [Edison] use:

    ```sh
    module load fftw
    ```
    or
    
    replace ```relion-1.3/INSTALL.sh``` with ```INSTALL_edison.sh```
    ```sh
    cd relion-1.3/INSTALL.sh
    ./INSTALL.sh
    ```
    
  - On [Hopper] use:

    ```sh
    git clone https://github.com/jjcorreao/relion.git
    ./INSTALL.sh target_dir
    ```
    
Batch jobs
----------------------------
Sample scripts to submit jobs to the queue can be found at ```scripts/```

```sh
qsub scripts/qsub.csh
export RELION_QSUB_EXTRA1="Max number of hours in queue"
export RELION_QSUB_EXTRA1_DEFAULT="72"
export RELION_QSUB_TEMPLATE="/gpfs/fs1/home/bioinfo/scheres/relion-0.9/bin/qsub.bash"
```

env

```sh
export LD_LIBRARY_PATH=/lmb/home/scheres/app/relion-1.3/lib:$LD_LIBRARY_PATH
export PATH=/lmb/home/scheres/app/relion-1.3/bin:$PATH
export RELION_QSUB_TEMPLATE="/lmb/home/scheres/app/relion-1.3/bin/qsub.csh"
export RELION_CTFFIND3_EXECUTABLE="/public/EM/CTFFIND/ctffind3.exe"
export RELION_RESMAP_EXECUTABLE="/public/EM/ResMap/ResMap-1.1.4-linux64"
```
    
```sh
#!/bin/bash
### Inherit all current environment variables
#PBS -V
### Job name
#PBS -N XXXnameXXX
### Keep Output and Error
#PBS -k eo
### Queue name
#PBS -q XXXqueueXXX
### Specify the number of nodes and thread (ppn) for your job.
#PBS -l nodes=XXXmpinodesXXX:ppn=XXXthreadsXXX
### Tell PBS the anticipated run-time for your job, where walltime=HH:MM:SS
###PBS -l walltime=XXXextra1XXX:00:00
#################################
### Switch to the working directory;
cd $PBS_O_WORKDIR
### Run:
mpirun --bynode -np XXXmpinodesXXX XXXcommandXXX
echo "done"
```

Interactive jobs with X forwarding
----------------------------
Run RELION in interactive mode using the GUI


[RELION]:
[NERSC]:
[Edison]:
[Hopper]: