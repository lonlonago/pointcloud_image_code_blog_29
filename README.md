#  First, the principle of the algorithm 

##  1. Scanning line extraction 

 ![avatar]( 20210529091811135.png) 

   At present, the laser scanners used in vehicle-mounted LiDAR systems are mainly linear scans, and the obtained scanning points are arranged according to the scanning line on the target. In urban environments or road environments, the top is mostly the sky, and the data obtained by the vehicle-mounted laser scanning system is distributed in a strip shape as a whole. The vehicle-mounted laser scanners mostly use panoramic scanning with a 360-degree field of view. As shown in Figure 1a, the points recorded by the vehicle-mounted laser scanning system are arranged in the order of laser pin point return. In the same scanning line, the scanning angle difference of successive laser pin points recorded by the system is a fixed value (usually the angular resolution of the laser scanner. In a complete scanning cycle, if the scanning field of view angle is the top sky, there will be no laser pin point return. At this point, the scanning angles of the last point of the current scan line and the starting point of the next scan line have an irregular step (and 2 consecutive laser pin points recorded for the system), as shown in Figure 1b. Likewise, because of the continuity of the onboard laser point cloud, when the scanning angle is the top sky inch, the GPS time difference will also have an irregular step. Therefore, an angle threshold or time value can be set, and the break points at both ends of the scanning line can be detected according to Equation 1 or 2, and the continuous point clouds can be classified into one scanning line, thereby converting the discrete scanning points into an ordered two-dimensional scanning line dataset.  

 ![avatar]( 20210529091823513.png) 

   Where and is the value of the scanning angle of the laser point, and the instantaneous GPS time, where and are the irregular change thresholds of the scanning angle difference and the time difference, respectively, which are related to the angular resolution and pulse frequency of the laser scanner. Figure 2 shows a vehicle-mounted laser point cloud data (2a). Using Equation 1 to determine two breakpoints in each scanning line according to a given angle difference threshold, the scanning line information of each point is extracted, and the discrete scanning points are organized into a series of ordered two-dimensional strips (2b). Figure 2 (b) In order to visually identify and distinguish the scanning lines, one display is selected every 50 scans.  

   As can be seen from Figure 2, the scanning lines extracted according to the time or scanning angle of the point cloud are basically along the driving direction of the vehicle, that is, at a certain angle with the trend of the road, and each scanning line is equivalent to a cross section of the road. Transforming the vehicle-mounted discrete point cloud into a series of ordered two-dimensional scanning line datasets is conducive to the rapid processing of the vehicle-mounted laser point cloud, and has the following advantages: 

##  2. References 

>  Fang Lina. Extraction of geometric features of road environment in vehicle laser point cloud [D]. Wuhan University, 2014.35-36. 

#  Code implementation 

##   main.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574263352
  ```  
##  1、MyPointCloud.h 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574263352
  ```  
##  2、ScanLineExc.h 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574263352
  ```  
##  3、MyPointCloud.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574263352
  ```  
##  4、ScanLineExc.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574263352
  ```  
#  III. Display of results 

 ![avatar]( b37bd1ce824e46f4a3a77c0c7b521741.png) 

##  IV. Remarks 

 1. The sampling interval of the above point cloud scanning lines is 20, and different colors are assigned to adjacent scanning lines to distinguish. 2. The setting of the time interval parameters is mainly based on the scanning frequency of the laser scanner or the analysis of the original point cloud time histogram. 3. Related links: Point cloud extraction scanning lines 



--------------------------------------------------------------------------------

#  Principle 

>  The PCL :: correspondences class has two members, query and match, which are the indexes of the corresponding point pairs on the source and target point clouds respectively. You can access the corresponding points in the source through source [query]; source [query] .x, source [query] .y, source [query] .z to access the x, y, z coordinates of the corresponding points of the source in the matching point pair. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574258254
  ```  
#  III. Display of results 

 ![avatar]( 20200502085925740.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Algorithm overview 

   Farthest Point Sampling (FPS): As the name suggests, the point farthest from the previously sampled points is selected for each sample. It can better ensure that the sampled points have good coverage, so it is widely used in the field of point cloud segmentation (e.g., PointNet ++, PointCNN, PointConv, PointWeb). However, the computational complexity of FPS is that the amount of computation is square related to the number of points in the input point cloud. This suggests that FPS may not be suitable for processing large-scale point clouds. For example, when entering a large field attraction cloud with millions of points, it takes up to 200 seconds to downsample it to 10% of the original size using FPS. 

##  2. Implementation process 

##  3. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427520
  ```  
 Note: This function was added to PCL1.13.0 

##  4. References 

>  [1] Hu Q , Yang B , Xie L , et al. RandLA-Net: Efficient Semantic Segmentation of Large-Scale Point Clouds[J]. 2019. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957427520
  ```  
#  III. Display of results 

 ![avatar]( 4f6ef957edfd4a95af260958d2ef035d.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 This bilateral filtering algorithm is only suitable for ordered point clouds. For the processing of disordered point clouds, please refer to: PCL Bilateral Filtering Based on Normal 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574185803
  ```  
#  III. Display of results 

 ![avatar]( 20210427214859188.png) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

 + 1. Enter data 

 + 2. Example 1, setInputCloud2, setIndices3, SearchSurface

 + 3. Code implementation 

#  Input data 

   Almost all classes in PCL inherit from the base class PCL :: PCL Base, and the PCL :: Feature class accepts input data in two different ways: 

 ![avatar]( 11a4b0d5bee05c4bd8fde1281bdd5196.png) 

   In addition, the set of point neighbors to use can be specified by an additional call, namely: setSearchSurface (PointCloudConstPtr &). This call is optional, and if no search surface is given, the input point cloud dataset is used by default. Because setInputCloud () is always required, we can use < setInputCloud (), setIndices, setSearchSurface () > to create four combinations at most. Suppose there are two point clouds, and. The following figure shows these four cases: setIndices () = false, setSearchSurface () = false No index, no specified search surface, search for the neighborhood of each point on the original point cloud entered in setInputCloud (). This is the most common case in PCL, where a feature is estimated at all points in the point cloud by simply entering a PointCloud dataset. Since developers don't want to maintain different implementation copies depending on whether a set of indexes and/or search surfaces is given, when indices = false, PCL creates a set of std :: vector < int > internal indexes pointing to the entire dataset.

      When using setSearchSurface (), the most useful case is: when there is a very dense input point cloud dataset, but we do not want to perform feature estimation at all points in it, but want to find some key points (using the method in the pcl_keypoints to estimate), or in the downsampled version of the point cloud (such as: using pcl :: Voxel Grid filtering) for feature estimation. In this case, we pass the downsampled point cloud/key points to the feature estimation algorithm through setInputCloud (), and set the original data source to the search set through setSearchSurface (), so as to improve the running efficiency of the program. 

#  Examples 

    Surface normal is an important property of a surface and is widely used in many fields. Here, taking normal estimation as an example, the calling codes of the above methods are given. 

##  1、setInputCloud 

 Computes a normal vector of all points in the input point cloud, taking into account the neighborhood located in setInputCloud for each point. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574233836
  ```  
##  2、setIndices 

 Computes the normal vector for the given index points, taking into account the neighborhood located in setInputCloud for each point. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574233836
  ```  
##  3、SearchSurface 

 Compute the normal vector for each point in a given point cloud (downsampled), considering for each point the neighborhood of the corresponding point in the SearchSurface 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574233836
  ```  


--------------------------------------------------------------------------------

#  First, the method introduction 

##  1. Find the corresponding point 

 ![avatar]( 20210414072519914.png) 

    PCL :: registration :: CorrespondenceEstimation is the base class to determine the correspondence between the target and the query point set (or feature). The input is the target and source point clouds, and the output is the point pair, which not only outputs the corresponding point set between the two sets of point clouds. Its inheritance relationship is shown in the figure.  

##  2. Main functions 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
##  3. Visualization of corresponding points 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
 1. Set the thickness of the corresponding point connection. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
 2. Set the color of the corresponding point connection, ranging from 0 to 1. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574132188
  ```  
##  result display 

##  1. Output correspondence 

 ![avatar]( 20200509221739981.png) 

##  2. Interactive search results 

 ![avatar]( 20200509221503372.png) 

##  3. Necessary instructions 

>  In the experiment, it is found that the output distance in the correspondence relationship is the square of the distance between the corresponding points 

 ![avatar]( 20200509222231918.png) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

#  I. Overview of algorithms 

   Generate a standard point cloud for some algorithm tests based on mathematical principles. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574249356
  ```  
#  III. Display of results 

 ![avatar]( 3dc529dc94124da4b5bb19ee44db2bc3.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

   By knowing the direction vector of a point and a straight line on a straight line, a standard straight line point cloud for algorithm testing can be generated according to mathematical principles. In the following example code, a point on a straight line is used as the center point to generate a spatial straight line point cloud, where the number of points is 100 and the interval between adjacent points is 0.1m. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574220583
  ```  
#  III. Display of results 

 ![avatar]( 20230926f49148c5a311ec53ec93fa11.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

 ![avatar]( c4d30b9f074e4e8aa817da634770a623.png) 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957429589
  ```  
#  III. Display of results 

 ![avatar]( 064c3e105c3c4c8eaaad728c21da52ce.png) 



--------------------------------------------------------------------------------

#  I. Overview of algorithms 

   Given a specified elevation value, get all points in the point cloud data with the same elevation. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957422441
  ```  
#  III. Display of results 

##  1. Primitive point cloud 

 ![avatar]( 254ad71c10ec4b99b28e7223df925b0a.png) 

   The original point cloud is rendered according to the elevation, and it can be seen that the distribution law of the point cloud coordinate elevation is as follows:  

>  For the method of point cloud rendering by elevation, see: CloudCompare - point cloud color rendering 

##  2. Get the results 

   In red are all the points at the specified elevation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 202402030957422441
  ```  
 ![avatar]( 02b348aea2984a6ca43a69bbae7990a6.png) 

#  IV. Experimental data 

 [1] 常用经典斯坦福点云数据 



--------------------------------------------------------------------------------

#  I. Introduction 

##  1. Overview 

    PCL pcl :: Point XY ZL is used to store xyz coordinates and label categorization label information data structure, PCL pcl :: Point XY ZL structure is: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574168118
  ```  
    The label attribute is of type uint32_t. The classification information in the LAS file classification is stored as uint8_t, as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574168118
  ```  
     uint8_t means 1 byte (1 byte = 8 bit), uint32_t means 4 bytes (4 bytes = 32 bit), just read it directly. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574168118
  ```  
#  III. Display of results 

 ![avatar]( 87fa92d6c8484dda81b7acf659aeb78a.png) 



--------------------------------------------------------------------------------

#  I. Introduction 

##  1. Overview 

    PCL pcl :: Point XYZ RGB is used to store xyz coordinates and RGB information data structure, PCL pcl :: Point XYZ RGB structure is: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
    For historical reasons (PCL was originally developed as a ROS package) RGB information is stored as an integer and converted to a floating-point number. RGB information in LAS files is stored as uint16_t, as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
    Therefore, to obtain RGB information from the LAS file using PCL, a corresponding data type conversion is required. 

##  2. Conversion method 

 You can use the following code snippet to package and decompress RGB colors into a PointXYZRGB structure: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
#  Code implementation 

##  1. Convert to RGB 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
##  2. Convert to r, g, b 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
##  3. Complete code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574188097
  ```  
#  III. Display of results 

 ![avatar]( 97c7b9856def4dad9f5c38bf30086a36.png) 



--------------------------------------------------------------------------------

#  I. Introduction 

##  1. Overview 

 ![avatar]( 46b74a23b51a40ba8e4c7b44f9223a8d.png) 

    The GPS time in the LAS file is a time tag value of type double for observing the point. The global coding low is cleared to GPS weekly time and set to GPS adjusted standard time. For aggregate model systems, the GPS time should be set to zero unless it is allocated from component measurements. The description of the official file is as follows: There is no point type in the PCL to save the GPS time, so a custom point type is required. For the method of customizing the point type, see: The PCL adds a custom point type. 

#  Code implementation 

##  1、GPSTime.h 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574123785
  ```  
##  2、GPSTime.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574123785
  ```  
##  3、main.cpp 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574123785
  ```  
#  III. Display of results 

 ![avatar]( 0460714d7cf640749514ba0b29afc363.png) 



--------------------------------------------------------------------------------

#  I. Introduction 

##  1. Overview 

    PCL pcl :: Po i nt XY ZI is a data structure used to store point cloud xyz coordinates and intensity information, where x, y, z and i are data of type float. The source code is as follows: 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574189391
  ```  
    The strengths in the LAS file are stored as unsigned short. Therefore, to get the strength of the point cloud from the LAS file, simply save the strengths in the LAS file to the pcl :: Point Cloud < pcl :: Point XYZ > container. 

##  2. Obtain strength from LAS 

 ![avatar]( 972e6f954d49450aabba474cc737d7b6.png) 

    The official document says that the intensity value is an integer representation of the pulse return amplitude. LasLib has lasReader- > point.get_intensity (); and lasReader- > point.intensity; for intensity acquisition. The official document describes it as follows:  

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574189391
  ```  
#  III. Display of results 

 ![avatar]( c2fc615c63c048c194592e0979dd6527.png) 



--------------------------------------------------------------------------------

#  Box filtering 

##  1. Algorithm overview 

    Given the maximum value of the box coordinates, extracts the points inside and outside the box. 

##  2. Main functions 

     PCL :: get Points In Box () forms a box and gets a set of points located within the box, given the maximum and minimum spatial coordinates. The function is the same as CropBox. 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574216273
  ```  
##  3. Function source code 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574216273
  ```  
#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574216273
  ```  
#  III. Display of results 

 ![avatar]( 18805b907aca4fd49327c2630b569779.png) 



--------------------------------------------------------------------------------

#  First, the principle of the algorithm 

##  1. Introduction to the algorithm 

>  Point cloud voxelization is a more common processing method for point clouds, pcl :: Voxel Grid and pcl :: ApproximateVoxelGrid voxelization method, the first of which is to obtain the point cloud center of gravity in each grid by dividing the voxel grid as the point cloud representative of the grid. The second is to represent the point cloud of the grid according to the center point of the grid. The pcl :: Grid Minimum class is to divide the three-dimensional point cloud into a grid in the X-Y plane, and then find the point with the smallest Z coordinate in each grid to represent the grid. If the grid does not have a point cloud, it will not generate a center point to represent the grid point cloud like pcl :: ApproximateVoxelGrid. 

##  2. Applicability 

>  PCL :: Grid Minimum can effectively filter the situation of discontinuous elevation information, such as vehicles parked under trees, etc., which can effectively find the lowest point and prepare for subsequent segmentation. However, if there are no vehicles under the tree or the ground point cannot be scanned, then the point of the grid may be the lowest point of the scanned leaves, which requires further processing. 

#  Code implementation 

  ```python  
After clicking on the GitHub Sponsor button above, you will obtain access permissions to my private code repository ( https://github.com/slowlon/my_code_bar ) to view this blog code. By searching the code number of this blog, you can find the code you need, code number is: 2024020309574133590
  ```  
##  1. Parameter settings 

   The only setting parameter of class GridMinimum is resolution_, which can be initialized by the constructor display, or the resolution can be set by the setResolution () function. This is related to the size of the mesh. The smaller the resolution, the denser the mesh division, and the larger the resolution setting, the sparser the mesh division. Class GridMinimum inherits FilterIndices < PointT > so you only need to set the resolution when the constructor is initialized to get the point cloud result after the mesh is minimized. 

#  III. Display of results 

 ![avatar]( 20210211193710206.png) 



--------------------------------------------------------------------------------

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



--------------------------------------------------------------------------------

