#  I. Overview of algorithms 

   The uniform sampling algorithm pcl :: Uniform Sampling in the PCL library is to perform voxelization on the point cloud, and then use the nearest neighbor point of each voxel to replace all the points in the voxel for sampling. This method requires the average calculation of the points in each voxel, and the extra computation makes the algorithm inefficient when dealing with large-scale scenic spot clouds. For the shortcomings of this algorithm, this blog implements every every_k_points points and samples one point. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574153782
  ```  
#  III. Display of results 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574153782
  ```  
 ![avatar]( 0171ad721ace42b994d25cd9d4718307.png) 

