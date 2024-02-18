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

