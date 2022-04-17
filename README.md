# Iris-recognition-Application-of-iris-recognition-for-biometric-authentication-
This project intends to identify humans based on iris using techniques of image processing.



1. INTRODUCTION :
A biometric system recognizes an individual automatically based on distinguishable 
characteristics an individual possesses. The quality of a biometrics depends on 
• How efficiently it can distinguish the most unique features from the sample so that 
two people having the same characteristics is minimized. 
• The extracted features must be stable so that they do not change over time. 
• The feature must be easy to extract. 

![image](https://user-images.githubusercontent.com/65909814/163697763-96362cce-9584-40f6-9ec8-ffe9a8635eff.png)

By definition, the iris is a thin, circular structure in the eye which is responsible for 
controlling the diameter of the pupil and by doing so it controls the amounts of lights are 
entering into the retina. Because of unique characteristics, iris recognition has widely accepted as a biometric to 
identify any individuals. By applying image processing technique, the unique pattern of 
the iris can be extracted from a digitized iris image and then save the extracted data for 
later matching.



   1.1 LITERATURE REVIEW :
First of all, an image will be taken of that particular person’s eye and then, the automated 
system will analyze the image. Thereafter, a template which contains unique features of 
that particular person. After generating the template, it will be stored in the database. 
Hence, this person is registered by iris recognition. Whenever he/she needs to validate 
his/her identity another image will be taken of his/her eye. A new template will be 
generated from this new image and will be matched with the reference template. If the 
system finds enough matching elements, then it will recognize the person and otherwise 
not. 



2. METHODOLOGY :

![image](https://user-images.githubusercontent.com/65909814/163697833-eedf7ed5-2294-4eec-bd1e-883ce122e52c.png)

![image](https://user-images.githubusercontent.com/65909814/163697856-98ffdbcc-6573-4716-a838-62279fdc9aea.png)

For iris recognition, at first, we need to find out the Iris region. In my iris recognition models 
we are finding iris and eyelids with the integrodifferential Daugman Operator. After 
successful segmentation of the iris region from the eye image, we need to transform this 
segmented region into a specific dimension in order to allow comparisons. 
The iris regions produced by automated normalization process must have same 
dimensions, so that two iris regions of the same eye will contains features at the same 
location. For the normalization process we are using Daugman’s Rubber Sheet Model.



2.1 Image Acquisition :
Iris image will be captured with highly sensitive equipment. Further, process depends on 
the quality of captured image. This phase is mere an image capture. But it is necessary to 
ensure that the method can overcome obstacles that frequently find in acquisition process 
which are blurry images, camera, diffusion, noise, light reflection and other things which 
may affects the segmentation process.

![image](https://user-images.githubusercontent.com/65909814/163697905-5b3f94e8-f40f-4086-b9b5-84494c1930b9.png)



2.2. Segmentation :
Iris recognition algorithm starts to work from this phase onward. Segmentation 
approximates the iris by two circles. One circle approximates iris boundary and second 
circle approximates pupil boundary as shown:

![image](https://user-images.githubusercontent.com/65909814/163697931-687aa2d4-9898-4be9-b5a7-aab3a63762c8.png)

Segmentation Algorithm
Daugman’s Integro-differential operator:
In Daugman’s algorithm, the circular iris and pupil region are detected by an integrodifferential operator and the eyelids and eyelashes are also detected by it. The equation 
of integro-differential operator is 

 ![image](https://user-images.githubusercontent.com/65909814/163697957-a3259393-64d1-49cc-8693-26c16eea9e78.png)

Where, 
I(x, y)Is the eye image
r is the radius 
Gσ(r)Is a Gaussian smoothing function? 
s Is the contour of the circle given by r, x0, y0 
By varying the value of radius and center coordinates, the operator searches for the 
circular path based on the maximum changes in pixel values.

Implementation of Segmentation Process:
Some pre-processing has to be done before this:
▪ Conversion to grayscale image

![image](https://user-images.githubusercontent.com/65909814/163697981-e6b17054-4d99-4c45-b84e-e44d5b33d159.png)

▪ Finding pupil centre coordinates and radius

![image](https://user-images.githubusercontent.com/65909814/163698033-493d2215-6a50-4940-87de-4cca69f2bf9e.png)

▪ Finding iris coordinates and radius



3. CROPPING :
• Create mask taking centre coordinate of pupil and radius
• Create mask taking centre coordinate of iris and radius

![image](https://user-images.githubusercontent.com/65909814/163698063-3dd40247-d81e-48b5-9282-51e28d8d07cd.png)

• Substract mask1 and mask2 to get single mask to apply on captured image
• Apply mask on image

![image](https://user-images.githubusercontent.com/65909814/163698074-e331029d-e374-4cf6-94fd-31396ae935f3.png)

4.NORMALIZATION
To normalize the segmented iris region Daugman [1] proposed a rubber sheet model 
which will remap all the Cartesian points in the iris region into polar coordinate (r, θ) 
system. 

![image](https://user-images.githubusercontent.com/65909814/163698105-73b4c7cf-53cd-4919-bcf6-649c0e33b167.png)

Figure 6: Daugman’s Rubber Sheet model.

To remapping the Cartesian coordinates to polar coordinates, the used equations are 
I(x(r, θ), y(r, θ)) → I(r, θ) x(r, θ) 
= (1− r)xp(θ) + rxl(θ) 
y(r, θ) = (1 − r)yp(θ) + ryl(θ) 
Here, I(x, y) is the Iris region Image and the original Cartesian coordinates are (x, 
y) and the corresponding polar coordinates are (r,θ). Moreover, (xp,yp) and (xl, yl) 
are the pupil and iris boundary coordinates along the θ direction. Pupil dilation and 
size inconsistent are also being in consideration to produce a normalized iris 
region. However, it doesn’t fall in with rotational inconsistencies. In Daugman’s Iris 
recognition and feature extracting algorithm, the rotation is compensated by 
shifting the iris template in the θ direction.

Implementation: 
▪ Mapping- Conversion of polar to rectangular conversion to get pattern

![image](https://user-images.githubusercontent.com/65909814/163698119-b2eacb55-ffce-435d-af24-c4626ce96445.png)

Figure 10: Extracted iris image Figure 11: Generated Pattern

• Taking mean as 4.5 and standard deviation 4.3 we plot the pattern

![image](https://user-images.githubusercontent.com/65909814/163698130-45895442-d729-437f-af0c-39a11f0a86e2.png)
 
![image](https://user-images.githubusercontent.com/65909814/163698162-3d1397d0-bfb3-41d6-bd8f-db0f1943ad44.png)

![image](https://user-images.githubusercontent.com/65909814/163698176-4d639db5-db47-4b1f-8a3c-6458fcf98a7e.png)



9. APPLICATIONS:
• National border controls: the iris as a living passport
• computer login: the iris as a living password
• cell phone and other wireless-device-based authentication
• secure access to bank accounts at cash machines
• ticketless travel; authentication of rights to services
• premises access control (home, office, laboratory, etc)
• driving licenses; other personal certificates.
• entitlements and benefits authorization.
• forensics; birth certificates; tracing missing or wanted persons.
• credit-card authentication.
• automobile ignition and unlocking; anti-theft devices.
• anti-terrorism (e.g.security screening at airports).
• secure financial transactions (electronic commerce, banking).
• Enter any existing use of keys, cards, PINs, or passwords.
• net security; control of access to privileged information.



11. REFERENCES:
[1] J. Daugman. How iris recognition works. Proceedings of2002 International Conference on 
Image Processing, Vol. 1, 2002. 
[2] E. Wolff. Anatomy of the Eye and Orbit. 7th edition. H. K. Lewis & Co. LTD, 1976. 
[3] R. Wildes. Iris recognition: an emerging biometric technology. Proceedings of the IEEE, Vol. 
85, No. 9, 1997. 
[4] J. Daugman. High confidence visual recognition of persons by a test of statistical independence. 
IEEE Transactions on Pattern Analysis and Machine Intelligence, Vol. 15, No. 11, 1993. 
[5] J.H.Doggart, Ocular Signs in Slit-Lamp Microscopy, Kimpton (1949), page 27 
[6] R. Wildes, J. Asmuth, G. Green, S. Hsu, R. Kolczynski, J. Matey, S. McBride. A systemfor 
automated iris recognition. Proceedings IEEE Workshop on Applications of Computer Vision, 
Sarasota, FL, pp. 121-128, 1994. 
[7] S. Lim,K. Lee, O. Byeon, T. Kim.Efficient iris recognition through improvement of feature vector 
and classifier. ETRI Journal, Vol. 23, No. 2, Korea, 2001. 
[8] C. Tisse, L. Martin, L. Torres, M. Robert. Person identification technique using humaniris 
recognition. International Conference on Vision Interface, Canada, 2002. 
[9] W. Kong, D. Zhang. Accurate iris segmentation based on novel reflection and eyelash detection 
model. Proceedings of 2001 International Symposium on Intelligent Multimedia, Video and 
Speech Processing, Hong Kong, 2001. 
[10] L. Ma, Y. Wang, T. Tan. Iris recognition using circular symmetric filters. National Laboratory 
of Pattern Recognition, Institute of Automation, Chinese Academy of Sciences, 2002

