# EXP 2 : Linear and Circular Convolution

## AIM: 

 To perform Linear and Circular Convolution for two given sequence using SCILAB. 

## APPARATUS REQUIRED: 
PC installed with SCILAB. 

## PROGRAM (Linear Convolution): 
```
clc;
clear;
close;
x = [1, 2, 3]; 
h = [4, 5, 6];    
disp("Input sequence x[n]:");
disp(x);
disp("Input sequence h[n]:");
disp(h);
L = length(x);
M = length(h);

disp("PART A: LINEAR CONVOLUTION");

N_linear = L + M - 1;
x_padded = [x, zeros(1, N_linear - L)];
h_padded = [h, zeros(1, N_linear - M)];

disp("Length for Linear Convolution (L+M-1): " + string(N_linear));
disp("Padded x for linear convolution:");
disp(x_padded);
disp("Padded h for linear convolution:");
disp(h_padded);
X_dft = fft(x_padded);
H_dft = fft(h_padded);
Y_dft = X_dft .* H_dft;
y_linear_dft = ifft(Y_dft);
y_linear_dft = real(y_linear_dft);
disp("Linear Convolution Result (DFT Method):");
disp(y_linear_dft);
y_linear_direct = conv(x, h);
disp("Linear Convolution Result (Direct using conv()):");
disp(y_linear_direct);
disp("-----------------------------------------------");
```
## PROGRAM (Circular Convolution): 
```
// Circular Convolution
clc; clear;

// Input sequences
x1 = input("Enter the first sequence x1: "); // e.g., [1 2 3]
x2 = input("Enter the second sequence x2: "); // e.g., [4 5 6]

// Make both sequences equal length by zero-padding
N = max(length(x1), length(x2));
x1 = [x1, zeros(1, N-length(x1))];
x2 = [x2, zeros(1, N-length(x2))];

// Compute DFTs
X1 = fft(x1, -1);
X2 = fft(x2, -1);

// Multiply in frequency domain
Y = X1 .* X2;

// Compute IDFT to get circular convolution
y_circ = fft(Y, 1); // IDFT
y_circ = real(y_circ); // Take real part

disp(y_circ, "Circular Convolution y(n) =");

// Plot input and output sequences using stem-style plots
scf(1); // Figure 1
subplot(3,1,1);
xpoly(0:N-1, x1, 0, 1);
xtitle("Input sequence x1(n)");

subplot(3,1,2);
xpoly(0:N-1, x2, 0, 1);
xtitle("Input sequence x2(n)");

subplot(3,1,3);
xpoly(0:N-1, y_circ, 0, 1);
xtitle("Circular Convolution y(n)");

```

## OUTPUT (Linear Convolution): 

<img width="908" height="757" alt="image" src="https://github.com/user-attachments/assets/e8ffc519-0676-4bc9-832f-c13e73d7d84d" />


## OUTPUT (Circular Convolution): 

<img width="815" height="931" alt="image" src="https://github.com/user-attachments/assets/6e3b4510-7d2e-478c-a229-91bf686b3ed5" />


## RESULT: 

Linear and Circular Convolution for two given sequence using SCILAB was performed.
