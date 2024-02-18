#  First, the principle of the algorithm 

##  1. Overview 

   The method for calculating the normal vector of point clouds in PCL adopts the matrix factorization method in the Eigen library. When reading the Open3D source code, it is found that Open3D integrates a method for quickly calculating the normal vector. The method adopts the numerical optimization algorithm mentioned in the literature A robust algorithm for finding the eigenvalues and eigenvectors of 3 × 3 symmetric matrices. Careful study of this paper will find that its calculation process coincides with the theoretical method in modern measurement adjustment!!!! 

##  2. References 

>  Scherzinger W M, Dohrmann C R. A robust algorithm for finding the eigenvalues and eigenvectors of 3 × 3 symmetric matrices [J]. Computer Methods in Applied Mechanics & Engineering, 2008, 197 (45-48): 4007-4015. [2] Wang Luyao, Liu Guolin, Wang Fengyun, Wang Ke, Han Yu. Separable nonlinear least squares problem solving method based on matrix factorization and its application [J]. Chinese Journal of Surveying and Mapping, 2022, 51 (11): 2317-2327. 

#  Code implementation 

 NormalEstimation.hpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574146858
  ```  
 main.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574146858
  ```  
#  III. Display of results 

 ![avatar]( d6bf53816867401fab9fa82b5aa6ca37.png) 

