# HLS_DFT 
HLS program for CORDIC   
Date: 2020/12/22   

Author: D06943001 Yi-Yen Hsieh   
Mail: D06943001@ntu.edu.tw   

Reference: https://github.com/KastnerRG/pp4fpgas

## Project Description
This project aims at building a COordinate Rotation DIgital Computer (CORDIC) DSP unit. It is a simple and efficient algorithm to calculate some nonlinear functions such as trigonometric functions, hyperbolic functions, square roots, or perform general arithematic calculation, for example: multiplications, divisions, and exponentials and logarithms with arbitrary base, typically converging with one digit (or bit) per iteration. CORDIC is therefore also an example of digit-by-digit algorithms. 

## HLS Optimization
original file: dft.c, dft_precompute.c, dft_unroll_inner2.c
the modified file by my own is ```dft_pipeline.c```

in the file ```dft_pipeline.c```
```c
```