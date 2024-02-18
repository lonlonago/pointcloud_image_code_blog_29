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
