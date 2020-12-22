# HLS_CORDIC
HLS program for CORDIC   
Date: 2020/12/22   

Author: D06943001 Yi-Yen Hsieh   
Mail: D06943001@ntu.edu.tw   

Reference: https://github.com/KastnerRG/pp4fpgas

## Project Description
This project aims at building a COordinate Rotation DIgital Computer (CORDIC) DSP unit. It is a simple and efficient algorithm to calculate some nonlinear functions such as trigonometric functions, hyperbolic functions, square roots, or perform general arithematic calculation, for example: multiplications, divisions, and exponentials and logarithms with arbitrary base, typically converging with one digit (or bit) per iteration. CORDIC is therefore also an example of digit-by-digit algorithms. 

## HLS Optimization
original file: cordic.cpp, cordic.h
the modified file by my own is ```cordic_unroll.cpp```

in the file ```cordic_unroll.cpp```
```c
  // This loop iteratively rotates the initial vector to find the
  // sine and cosine values corresponding to the input theta angle
  for (int j = 0; j < NUM_ITERATIONS; j++) {
	  #pragma HLS unroll
      // Determine if we are rotating by a positive or negative angle
      int sigma = (theta < 0) ? -1 : 1;

      // Multiply previous iteration by 2^(-j)
      COS_SIN_TYPE cos_shift = current_cos * sigma * factor;
      COS_SIN_TYPE sin_shift = current_sin * sigma * factor;

      // Perform the rotation
      current_cos = current_cos - sin_shift;
      current_sin = current_sin + cos_shift;

      // Determine the new theta
      theta = theta - sigma * cordic_phase[j];

      factor = factor / 2;
  }
```