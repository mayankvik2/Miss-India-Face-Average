# Miss-India-Face-Average
![alt text](https://github.com/mayankvik2/Miss-India-Face-Average/blob/master/Miss%20India%20Grand%20Finale.jpg)

In this post I wrote a Python script to Generate Virtual Miss India by face average top 3 finalist of Femina Miss India 2018 with images of Anukreethy Vas, Meenakshi Chaudhary, Shreya Rao Kamavarapu. The motivation for doing the project came for  amusing experiment researchers averaged the faces of 22 miss Germany finalists of 2002.I have referred URL for Virtual Miss Germany also.

1.	Detecting facial landmarks of  Images using Dlib  68 point landmark Detector: Dlib’s facial landmark or features detector is done on two parts, first detect face from the image and output rectangle of face detector and second landmark detector finds facial features inside the face rectangle

2.	Coordinate Transformation: The input facial images can be of very different sizes. So we need a way to normalize the faces and bring them to the same reference frame. To perform this I warp to transform 4137*2975 to 600×600 image I used Similarity Transform by OpenCV’s estimateRigidTransform requires 3 points for calculating similarity matrix.

3.	Face Alignment: After similarity transform all images are of same size but to calculate the average face where the features are aligned, we first need to calculate the average of all transformed landmarks in the output image coordinates by:

i.	Finding the Delaunay Triangulation: Delaunay triangulation allows us to break the image into triangles so I will use 68 points facial points and 8 points on the boundary of the output image 
 

ii.	Finding Affine warp triangles: An Affine warp triangle transforms a set of 3 points of a triangle to another set of arbitrary 3 points of triangle. It covers all above necessary requirements of translation rotation , scaling and translation

4.	Now  for calculating the average image, simply add the pixel intensities of all warped images obtained from previous step and divide by the number of images and store this mean shape in a vector and the 8 boundary point of the output image is added to vector

![alt text](https://github.com/mayankvik2/Miss-India-Face-Average/blob/master/FinalMissIndia2.PNG)



