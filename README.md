# Programming paradigms for GPU devices

Online edition 15-17 April 2020


## Download/Clone repository

```bash
git clone https://gitlab.hpc.cineca.it/training/gpu-programming-2020.git
```

## Slides

The slides are available in PDF format
```bash
cd slides
```

## Hands-on Sessions

Hands on sessions will be held on **GALILEO** cluster at CINECA.  
For a detailed guide on GALILEO cluster see
[here](https://wiki.u-gov.it/confluence/display/SCAIUS/UG3.3%3A+GALILEO+UserGuide).

In order to login on GALILEO cluster for the hands-on sessions
a valid username (akin `a08trbXX`) and password are sent to you by email.

You can connect to a GALILEO login node using SSH connection:
```
ssh a08trbXX@login.galileo.cineca.it
```
where XX is in the range {01, ... , 50} and it is the username sent to you by mail.

Please complete and compile the exercises on **login node**.  
Once you have completed the exercise you can request a GPU resource on a **compute node** to run it.

If you want to run on a dedicated GPU, ask the scheduler for GPU resourses using:
```
srun -X -t 10 -N 1 --ntasks-per-node 4 --gres=gpu:kepler:1 -p gll_usr_gpuprod -A tra20_cgpu --reservation s_tra_gpu --pty "/usr/bin/bash"
```
Within this command you reserve a GPU on a compute node of GALILEO for 10 minutes.

In order to avoid to repeat the `srun` command you can source the `get_gpu` file located in the root directory of repository
and an alias to the `srun` command is created.  
Therefore , first:
```
source get_gpu
```
Once you have sourced the `get_gpu` file you can simply reserve a GPU with the following alias:
```
get_gpu
```

**NB**: Please do **NOT** use **login node** to run your exercises but use **compute node**.
login node is only used to complete source code and compile it.


## Exercises

A skeleton of exercises are provided.  
At the end of course the **solutions** of all exercises are published in the repository.


## **OpenACC** exercises

```bash
cd hands-on/openacc
```

#### Load PGI Environment

```bash
module load profile/advanced
module load pgi
module load cuda
```

#### Show loaded environment
```bash
module list
```

### Complete exercise skeleton

Open the source code and complete the exercise by adding OpenACC directives.

If you prefer to use C/C++ language complete the source file `laplace2d.c`.  
Instead if you prefer to use Fortran launguage complete the source file `laplace2d.F90`.

A Makefile is available to facilitate the compilation process.

If you are a C/C++ user compiles with command:
```
make pgi_c
```

Insted Fortran users should use command:
```
make pgi_f90
```


## **CUDA** exercises

```bash
cd hands-on/cuda
```

You can use both C/C++ and Fortran for CUDA hands-on session.  
For C/C++ exercises you can choose **GNU** or **PGI** environment.  
If you are a **Fortran** user you have to load **PGI** environment in order to use CUDA-FORTRAN.

All exercises are skeleton to complete.  
You have to insert CUDA/CUDA-FORTRAN code to complete exercises where you find comment like
```
INSERT CUDA CODE HERE
```

For each exercises a `Makefile` is presented to help you to compile the exercises.

#### Load GNU Environment

```bash
module load profile/advanced
module load gnu
module load cuda
```

#### Load PGI Environment

```bash
module load profile/advanced
module load pgi
module load cuda
```

#### Show loaded environment
```bash
module list
```


### 2<sup>nd</sup> Day CUDA Exercises

You find proposed exercises in `hands-on/cuda` directory.

1. See and compile **simple examples** in CUDA/CUDA-FORTRAN   
   `VectorAdd`   
   `MatrixAdd` 

2. Complete **Matrix Multiplication** example and annotate the kernel performance  
   `MatrixMul`

3. Collect **Bandwidth** test results


### 3<sup>rd</sup> Day CUDA Exercises

You find proposed exercises in `hands-on/cuda` directory.

1. Complete Matrix Multiplication example using **Shared Memory** and annotate kernel performance  
   `MatrixMulShared`

2. Complete and compare performance of **CUDA Streams** exercises  
   `Streams`

