MPI Tutorial
============

This is the static webpage and code for mpitutorial.com. View mpitutorial.com/about/ for guidelines on how to contribute tutorials, or feel free to open a pull request to fix any issues.

For those that simply wish to view MPI code examples without the site, browse the tutorials/*/code directories of the various tutorials. The tutorials/run.py script provides the ability to build and run all tutorial code.


#MPI Examples on Koding : http://mpitutorial.com/tutorials/

The whole process takes about half and hour:

##Part One: Installation of MPI

1. get source code from http://www.mpich.org/
    `$ wget http://www.mpich.org/static/downloads/3.1.4/mpich-3.1.4.tar.gz`

2. make a folder for mpi installation, using `mkdir` make a folder as `/home/mpi/mpich-3.1.4/src`

3. copy your mpich-3.1.4.tar.gz to `/home/mpi/mpich-3.1.4/src`
   `$ cp mpich-3.1.4.tar.gz  /home/mpi/mpich-3.1.4/src/`

4. unzip the using `$ tar -zxvf mpich-3.1.4.tar.gz`

5. enter the installation directory, using `$ cd /home/mpi/mpich-3.1.4/src/mpich-3.1.4`

6. configuration: `$ ./configure –prefix=/home/mpi/mpich-3.1.4`

7. compile MPI
   ```
   $ sudo make
   $ sudo make install
   ```
   
9. enviroment setting in `~/.bash_profile`

    `$ vim ~/.bash_profile` and then add the following setting into the file:

    ```
    export MPI_ROOT=/home/mpi/mpich-3.1.4
    export PATH=$MPI_ROOT/bin:$PATH
    export MANPATH=$MPI_ROOT/man:$MANPATH
    ```

 10. test for the installation path setting

    ```
    $ source ~/.bash_profile
    user_name: /home/mpi/mpich-3.1.4/src/mpich-3.1.4 $ which mpicc
    /home/mpi/mpich-3.1.4/bin/mpicc
    user_name: /home/mpi/mpich-3.1.4/src/mpich-3.1.4 $ which mpirun
    /home/mpi/mpich-3.1.4/bin/mpirun
    ```

 11. go to example folder and test

    ```
    user_name: /home/mpi/mpich-3.1.4/src/mpich-3.1.4/examples $ mpicc cpi.c -o cpi
    user_name: /home/mpi/mpich-3.1.4/src/mpich-3.1.4/examples $ mpirun -n 8 ./cpi

    Process 2 of 8 is on user_name
    Process 6 of 8 is on user_name
    Process 5 of 8 is on user_name
    Process 0 of 8 is on user_name
    Process 3 of 8 is on user_name
    Process 1 of 8 is on user_name
    Process 4 of 8 is on user_name
    Process 7 of 8 is on user_name
    pi is approximately 3.1415926544231247, Error is 0.0000000008333316
    wall clock time = 0.099858
   ```
   
   
##Part 2: Run Sample Examples

1. go to your working directory on Koding

   `$ cd /home/user_name/`

2. clone the tutorial from github

   ```
   $ git clone https://github.com/wesleykendall/mpitutorial
   $ cd mpitutorial/tutorials/mpi-hello-world/code`
   ```
   
3. compile and run

   ```
   $ sudo make
   $ cd  ~/mpitutorial/tutorials 
   ```
   - mpi-helloworld tutorial
   ```
   $ mpirun -n 4  ./mpi-hello-world/code/mpi_hello_world
   Hello world from processor user_name, rank 1 out of 4 processors
   Hello world from processor user_name, rank 3 out of 4 processors
   Hello world from processor user_name, rank 2 out of 4 processors
   Hello world from processor user_name, rank 0 out of 4 processors
   ```
   - mpi-send-and-receive tutorial
   ```
   $ mpirun -n 2  ./mpi-send-and-receive/code/send_recv
   Process 1 received number -1 from process 0
   ```
   
   - dynamic-receiving-with-mpi-probe-and-mpi-status tutorial
   ```
   $ mpirun -n 2 ./dynamic-receiving-with-mpi-probe-and-mpi-status/code/check_status
   0 sent 5 numbers to 1
   1 received 5 numbers from 0. Message source = 0, tag = 0
   ```
