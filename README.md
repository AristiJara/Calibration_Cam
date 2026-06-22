# Camera Calibration with OpenCV
**Authors:** Aristides Jaramillo

Camera calibration project using OpenCV based on the pinhole camera model. The project covers chessboard corner detection, intrinsic and extrinsic parameter estimation, lens distortion correction, and dual-camera calibration.

---

## About the project

The pinhole camera model describes how 3D points in space are projected onto a 2D image plane. Camera calibration determines the intrinsic parameters (focal lengths and principal point) and distortion coefficients (radial and tangential) that characterize a camera's optical system. This project applies OpenCV's calibration pipeline to two cameras using chessboard images.

### Key concepts

**Intrinsic parameters** — Focal lengths (fx, fy) and principal point (cx, cy), fixed for a given camera regardless of image resolution.

**Lens distortion** — Radial distortion (coefficients k₁, k₂, k₃) causing barrel or pincushion effects, and tangential distortion (p₁, p₂) from lens misalignment.

---

## Experiments

### Chessboard Corner Detection
Calibration images of an 8×5 chessboard (2.8 cm squares) are processed to detect internal corners using `cv.findChessboardCorners`, refined to subpixel accuracy with `cv.cornerSubPix`.

### Camera Calibration
3D world points and their 2D image projections are used to compute the camera matrix and distortion coefficients via `cv.calibrateCamera`. Results are saved as `.npz` files for reuse.

### Distortion Correction
Calibration parameters are loaded and applied to raw images using `cv.undistort`, producing corrected output images.

### Reprojection Error
Mean reprojection error is computed to assess calibration quality. A value below 0.5 pixels is considered acceptable.

### Dual-Camera Calibration
Calibration was performed independently for two cameras, obtaining their respective camera matrices and distortion coefficients.

---

## Results

| Camera | fx | fy | cx | cy |
|--------|----|----|----|----|
| Camera 1 | 702.48 | 702.64 | 943.49 | 514.73 |
| Camera 2 | 730.39 | 730.74 | 947.95 | 521.05 |

Mean reprojection error: **0.164 pixels**

---

## Technologies

- Python
- OpenCV
- NumPy / Matplotlib
- Google Colab / Google Drive

---

## References

- [OpenCV — Camera Calibration](https://docs.opencv.org/4.x/d9/d0c/group__calib3d.html)
- [OpenCV — Camera Calibration Tutorial](https://docs.opencv.org/4.x/dc/dbb/tutorial_py_calibration.html)
