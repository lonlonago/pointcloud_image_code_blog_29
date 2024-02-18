#  First, the principle of the algorithm 

##  1. Overview of the principle 

    Gaussian filtering takes advantage of the characteristics of Gaussian function after Fourier transform. Let the weight of the specified area be Gaussian distribution, so as to filter out high-frequency noise points. Specifically, a data point is weighted and averaged with each data point before and after, and those points that are much larger than the operating distance are processed into fixed endpoints, which helps to identify gaps and endpoints. Because the average effect of Gaussian filtering is small, it can better maintain the original appearance of the data while filtering, so it is often used. 

##  2. Implementation process 

    The main principle of Gaussian filtering of point clouds is to remove noise points based on statistical methods. According to the point cloud density near the sampling point, it is determined whether it is a noise point. If the point cloud data of a certain block is less than a certain density, the point cloud is removed. The point cloud density is obtained by analyzing the distance between the point cloud data and the neighborhood points statistically. The algorithm flow is based on KD-Tree to search for the neighborhood points around each point cloud data in turn, and calculate the average Euclidean distance from the sampling points to their neighborhood points. The larger the value setting, the better the processing effect, and the amount of calculation will suddenly increase, making it inefficient. Then set the size as appropriate through the actual situation. Set = {} as the original point cloud data. The dataset after KD-Tree search is = {}. Defined as the average distance from the obtained points to their neighborhood points, which is the mean of, and the standard deviation of, there is the following formula: The distances of all point clouds in the point cloud should form a Gaussian distribution. Given the mean and variance, the noise reduction effect can be achieved. 

##   3. References 

>  [1] PCL :: filters :: Convolution 3D and pcl :: filters :: Gaussian Kernel class provides the implementation of this algorithm. [2] Many papers mention adding Gaussian noise to point clouds, please refer to my other blog - PCL point clouds add Gaussian noise and save [3] Li Liuyi, Zhu Yufeng. Research on point cloud data noise reduction algorithm based on hybrid filtering [J]. Jiangxi Science, 2021, 39 (03): 525-529 + 533. 

#  Code implementation 

 test data 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574264261
  ```  
#  III. Display of results 

 ![avatar]( 20201109100643770.png) 

