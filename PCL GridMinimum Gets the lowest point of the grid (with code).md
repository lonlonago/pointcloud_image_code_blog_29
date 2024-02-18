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

