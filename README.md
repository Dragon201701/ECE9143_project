# ECE9143 HPML Final Project
**Accelerating Number Theoretic Transform for High-performance privacy preserving machine learning using Nvidia GPU**
## Abstract
In today’s high performance machine learning system where privacy concerns start arising, the gap between HE and machine learning must be bridged. Privacy concerns have thrust privacy-preserving computation into the spotlight. Homomorphic encryption (HE) is a cryptographic system that enables computation to occur directly on encrypted data, providing users with strong privacy (and security) guarantees while using the same services they enjoy today unprotected. While promising, HE has seen little adoption due to extremely high computational overheads, rendering it impractical. Previous research shows that the Number Theoretic Transform (NTT) is one of the bottle necks for the high-performance privacy preserving machine learning system. In this project, I will accelerate this algorithm using CUDA on Nvidia GPUs. 

## How to run the code:

Navigate to each folder. Open the header file to change the hyperparameters such as maximum number of threads and maximum number of blocks launched each time kernel is invoked. Finally, follow these commands:
``` Bash
make clean
make all
./ntt
```
Results are measured on CUDA 11.6 and CUDA 11.3 on Ubuntu 20.04 system with nvidia driver version 470.19. Hardwares are GTX1080 and Intel i7 8700 with 32GB mem.  

## Main Result
| maxthreads | inplace_dif | inplace_dit | pease    |
|------------|-------------|-------------|----------|
|          1 |      3.1673 |     3.13434 | 0.253502 |
|          2 |     1.68092 |     1.68709 | 0.250495 |
|          4 |    0.831348 |     1.01629 | 0.234751 |
|          8 |    0.472502 |    0.641575 | 0.295248 |
|         16 |    0.348652 |     0.51664 | 0.228345 |
|         32 |     0.23294 |    0.403408 | 0.235941 |
|         64 |    0.185696 |    0.382066 | 0.232705 |
|        128 |    0.156169 |    0.336544 | 0.235728 |
|        256 |    0.170691 |     0.32358 | 0.234253 |
|        512 |    0.186446 |    0.338545 | 0.255258 |
|       1024 |    0.237379 |    0.408641 | 0.255612 |

Table 1 Total time for CUDA implementation using memory copy in ms

| Total time memcpy (ms) | Total time sharedmem (ms) | Algo        |
|------------------------|---------------------------|-------------|
|               0.186446 |                  0.224256 | inplace_dif |
|               0.338545 |                  0.108614 | inplace_dit |
|               0.255258 |                  0.329698 | pease       |

Table 2 Total time for different algorithm using maximum threads of 512

| Total time memcpy (ms) | Total time sharedmem (ms) | Algo        |
|------------------------|---------------------------|-------------|
|               0.237379 |                  0.227119 | inplace_dif |
|               0.408641 |                  0.132228 | inplace_dit |
|               0.255612 |                  0.308603 | pease       |

Table 3 Total time for different algorithm using maximum threads of 1024

## Future Work: 
[NTTSuite](https://github.com/Dragon201701/NTT_Xilinx)
## Acknowledgements
This work was supported in part by the Applications Driving Architectures (ADA) Research Center, a JUMP Center co-sponsored by SRC and DARPA. This research was also developed with funding from the Defense Advanced Research Projects Agency (DARPA),under the Data Protection in Virtual Environments (DPRIVE) program, contract HR0011-21-9-0003. The views, opinions and/or findings expressed are those of the author and should not be interpreted as representing the official views or policies of the Department of Defense or the U.S. Government.
