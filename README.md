
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
    
[RELION]:
[NERSC]:
[Edison]:
[Hopper]: