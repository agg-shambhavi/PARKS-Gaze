## PARKS-Gaze - Github page for the details and access of PARKS-gaze Dataset

We provide an In-the-Wild gaze estimation dataset PARKS-Gaze. 

- PARKS-Gaze contains 300,961 images of 28 subjects. We divide the dataset into Train, Valid and Test splits ensuring similar head pose and gaze distribution in all three splits. The number of subjects in Train, Valid and Test splits are 18, 4, and 6. 

- The dataset was collected in both indoor and outdoor environments, covering a wide range of  head poses, illumination conditions and intra-person appearance variations. 

- We provide the dataset in two formats. In one format, normalized face crop of size 120x120 along with the eye crop size of 36x60 are provided. In another format, normalized face crop of size 3x224x224 alone are provided without eye crops. We chose to release in these formats as most of the existing methods / approaches adopt one of these input sizes. 

## Dataset Structure
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



In the format where a normalized face crop of 120x120 and left and right eye crops are present, a generic session_x.h5 file contains dictionaries with below keys.

- Norm_Face: Contains normalized face crops of that session (size 120x120).
- FixationID: IDs of fixations of interest, identifying key fixations during the session.
- Norm_gaze: Normalized gaze data representing where the participant was looking.
- Norm_hp: Normalized head pose data, useful for understanding the head orientation.
- GazePt_Px: Gaze points in pixel coordinates.
- GazePt_mm: Gaze points in millimeter coordinates, providing a physical measurement of gaze points.
- FcCenter: Data representing the center of the face.
- FcRotMat: Rotation matrix of the face, useful for transforming coordinates.



 
 For any queries, feel free to write to: lrdmurthy@iisc.ac.in
 


Citation:

@article{lrd2023towards,
  title={Towards Precision in Appearance-based Gaze Estimation in the Wild},
  author={LRD, Murthy and Mukhopadhyay, Abhishek and Aggarwal, Shambhavi and Anand, Ketan and Biswas, Pradipta},
  journal={arXiv preprint arXiv:2302.02353},
  year={2023}
}

Dataset Structure:

---Train
	|
	|
