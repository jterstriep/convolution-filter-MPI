# Applying a convolution filter to an image in parallel using MPI
This project was developed for the university course Parallel Systems as an introduction to parallel
computing using the Message Passing Interface (MPI) and the OpenMP API.

## Convolution filter
In image processing, a convolution filter (also called kernel, convolution matrix or mask) is used to transform
an image by applying an effect such as blurring, sharpening, embossing, edge-detection, and more.

The computation revolves around calculating the value of each pixel of the output image, given an input image
and a convolution matrix.

## Why make it parallel
The computation of the value of the *i-th* output pixel is based on the value of the input pixel *i* and it's
surrounding pixels. This shows that we should exploit the locality on the computations needed.  
In fact, if the filter is a *3x3* matrix, in order to compute the output values of a rectangular (*NxM*) part of the original image, there is only need for the adjacent pixels, which are *2x(N+2)* for the upper and lower rows plus *2x(M+2)* for the right and left columns. Due to this property of the problem, a parallel approach was a good candidate. 
