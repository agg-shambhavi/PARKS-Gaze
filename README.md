# PARKS-Gaze - Github page for the details and access of PARKS-gaze Dataset

We provide an In-the-Wild gaze estimation dataset PARKS-Gaze. 

- PARKS-Gaze contains 300,961 images of 28 subjects. We divide the dataset into Train, Valid and Test splits ensuring similar head pose and gaze distribution in all three splits. The number of subjects in Train, Valid and Test splits are 18, 4, and 6. 

- The dataset was collected in both indoor and outdoor environments, covering a wide range of  head poses, illumination conditions and intra-person appearance variations. 

- We provide the dataset in two formats. In one format, normalized face crop of size 120x120 along with the eye crop size of 36x60 are provided. In another format, normalized face crop of size 3x224x224 alone are provided without eye crops. We chose to release in these formats as most of the existing methods / approaches adopt one of these input sizes. 

# Dataset Structure
```
Parks-Gaze-Release.7z
├── Participant0
│   │── session_x.h5
│   │── session_y.h5
│   │── ...
│   │── ...
│   │── session_z.h5   
├── Participant1
│   │── session_x.h5
│   │── session_y.h5
│   │── ...
│   │── ...
│   │── session_z.h5   
├── Participant2
│   │── session_x.h5
│   │── session_y.h5
│   │── ...
│   │── ...
│   │── session_z.h5   
├── Participant3
│   │── session_x.h5
│   │── session_y.h5
│   │── ...
│   │── ...
│   │── session_z.h5   
├── ....
├── ....
├── ....
├── ....
├── Participant27
│   │── session_0.h5
│   │── session_1.h5
│   │── ...
│   │── ...
│   │── session_xx.h5   
```

# session_x.h5 File Structure

```
The attributes of each h5 file is a dictionary named "session_metadata" which contains the following necessary information about each session. 

- ParticipantID
- SessionID
- Intrinsic_Matrix : Camera Intrinsics Information
- Dist_Coeffs : Distortion coefficients of the camera (Used to undistort the images obtained using the camera during normalization)
- Screen_Resolution_X_mm : Width of the display (X direction) used in this particular session in millimeters
- Screen_Resolution_Y_mm : Height of the display (Y direction) used in this particular session in millimeters
- Screen_Resolution_X_px : Horizontal resolution of display used in this particular session in pixels
- Screen_Resolution_Y_px : Vertical resolution of display used in this particular session in pixels
- Camera_Screen_R : Extrinsic rotational matrix between camera and the screen coordinate systems
- Camera_Screen_T : Extrinsic translational vector between camera and the screen coordinate systems

In the format where a normalized face crop of 120x120 and left and right eye crops are present, a generic session_x.h5 file contains dictionaries with below keys.

- Norm_Face: Contains normalized face crops of that session (size 120x120).
- Norm_Leye: Contains normalized left eye crops of that session (size 36x60).
- Norm_Reye: Contains normalized right eye crops of that session (size 36x60).
- FixationID: Fixation IDs of the normalized samples available in this session. Each session recorded participants while making multiple fixations. Each fixation involves participant looking at a point on screen and making one of the following: head pose variation (position / orientation), facial expressions, activities like talking. 
- Norm_gaze: Normalized gaze data representing where the participant was looking. Format : [pitch, yaw]
- Norm_hp: Normalized head pose data, useful for understanding the head orientation.
- GazePt_Px: Gaze points in pixels (screen coordinate system).
- GazePt_mm: Gaze points in millimeters (screen coordinate system).
- FcCenter: Face center information of all normalized samples in the session. Format: [x, y, z], obtained as the average of the four eye corner landmarks using OpenFace 2.0 toolkit [1]
- FcRotMat: Rotation matrix of the face.


In the format where a normalized face crop of 224x224 is available, the left and right eye crops are not provided.


- For the task of 3D gaze estimation, one may use the Norm_Face, Norm_Leye and Norm_Reye along with Norm_gaze to train and evaluate the models. 

- For evaluating precision of the models on this dataset, one may transform the gaze predictions from the model (preds) to screen points using the python script "maptodisplay.py". The standard deviation across all predicted screen points corresponding to a single FixationID would be the precision error. 


```


## Train, Valid and Test Split Details:

```

Train
├── ParticipantIDs: 0, 1, 2, 3, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 23, 24, 25, 26 
Valid
├── ParticipantIDs: 6, 7, 11, 22 
Test
├── ParticipantID: 4, 5, 8, 9, 10, 27

```
	


For any queries, feel free to write to: lrdmurthy@iisc.ac.in
 


Citation:

@article{lrd2023towards,
  title={Towards Precision in Appearance-based Gaze Estimation in the Wild},
  author={LRD, Murthy and Mukhopadhyay, Abhishek and Aggarwal, Shambhavi and Anand, Ketan and Biswas, Pradipta},
  journal={arXiv preprint arXiv:2302.02353},
  year={2023}
}
