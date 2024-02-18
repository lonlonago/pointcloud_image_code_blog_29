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

