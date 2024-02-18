 ICP registration 

 + 1. Algorithm principle 

 + 1. Registration process 2. Algorithm derivation 3. References

 + 2. Code implementation 

 + 3. Results display 

 + 4. No adjustment library implementation 

#  First, the principle of the algorithm 

##  1. Registration process 

   ICP iteratively corrects the rigid body transformation (translation, rotation) of the two original point clouds to minimize the distance between all point sets. Input: Two frames of original point clouds, initial estimate of the transformation, standard for stopping iteration; Output: transformation matrix, modified point cloud after transformation. 

##  2. Algorithm derivation 

>  Description of ICP algorithm on PCL official website: How to use iterative closest pointICP algorithm detailed derivation process: 3D point cloud registration - ICP algorithm principle and derivation 

##  3. References 

>  [1] BESL P J, MCKAY N D. A method for registration of 3-Dshapes [J]. IEEE Transactions on Pattern Analysis and Machine Intelligence, 1992, 14 (2): 239-256. [2] Wang Fei, Liu Rufei, Ren Hongwei, Chai Yongning. Multi-phase vehicle laser point cloud registration using road target characteristics [J]. Journal of Surveying and Mapping Science and Technology, 2020, 37 (05): 496-502. [3] doc: How to use iterative closest point [4] PCL: pcl :: IterativeClosestPoint 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132822
  ```  
#  III. Display of results 

 ![avatar]( 20201111095343380.png) 

#  Fourth, do not adjust the library implementation 

 [1] ICP算法实现（C++） [2] ICP计算点集配准（C++、matlab代码） 

