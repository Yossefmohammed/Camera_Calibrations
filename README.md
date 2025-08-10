# Camera Calibrations Project

A comprehensive collection of camera calibration tools and 3D pose estimation implementations using OpenCV and Python. This project provides everything you need to calibrate cameras, extract intrinsic and extrinsic parameters, and perform 3D pose estimation for real-world applications.

## 📁 Project Structure

```
Camera_Calibrations/
├── Calibartion_Camera_with_checkerboard/     # Camera calibration using checkerboard
├── exract_intrinsic&&extrinsic_parameters/   # Parameter extraction and storage
├── 3D_pose-Estimation_camera-cliibration/    # 3D pose estimation with calibrated camera
├── head_Pose_Estimation/                     # Real-time head pose estimation
└── README.md
```

## 🎯 Project Components

### 1. Camera Calibration with Checkerboard
**Location**: `Calibartion_Camera_with_checkerboard/`

This module provides tools for camera calibration using a checkerboard pattern:

- **`colabration_checkerboard.ipynb`**: Main calibration notebook
- **`checkerboard.png`**: Generated checkerboard pattern (8x8)
- **`checkerboard_pattern_8x8.png`**: Alternative checkerboard pattern
- **`images/`**: Directory containing calibration images

**Features**:
- Automatic checkerboard pattern generation
- Real-time camera feed with checkerboard detection
- Interactive image capture (press 's' to save when checkerboard is detected)
- Visual feedback with corner detection overlay

**Usage**:
1. Run the notebook to generate a checkerboard pattern
2. Print the pattern and mount it on a flat surface
3. Use the camera capture tool to collect calibration images
4. Press 's' when the checkerboard is properly detected
5. Collect 10-20 images from different angles and distances

### 2. Intrinsic & Extrinsic Parameter Extraction
**Location**: `exract_intrinsic&&extrinsic_parameters/`

This module extracts and stores camera calibration parameters:

- **`EXTRACTING_WITh_checkerboard.ipynb`**: Parameter extraction notebook
- **`calib_data/`**: Directory containing calibration data
  - `MultiMatrix.npz`: Camera matrix, distortion coefficients, rotation and translation vectors
  - `calibration_data.npz`: Alternative calibration data format

**Features**:
- Automatic parameter calculation from calibration images
- Camera matrix (intrinsic parameters) extraction
- Distortion coefficients calculation
- Rotation and translation vectors (extrinsic parameters)
- Data storage in NumPy format for easy loading

**Parameters Extracted**:
- **Camera Matrix**: Focal length, principal point
- **Distortion Coefficients**: Radial and tangential distortion
- **Rotation Vectors**: Camera orientation
- **Translation Vectors**: Camera position

### 3. 3D Pose Estimation
**Location**: `3D_pose-Estimation_camera-cliibration/`

Advanced 3D pose estimation using calibrated camera parameters:

- **`#d_pose.ipynb`**: 3D pose estimation notebook
- **`output/`**: Directory for processed images with 3D overlays

**Features**:
- Uses calibrated camera parameters for accurate pose estimation
- Two visualization modes:
  - **Axes Mode**: Draws 3D coordinate axes (X, Y, Z)
  - **Cube Mode**: Draws a 3D cube on the checkerboard
- Batch processing of calibration images
- High-precision pose estimation using PnP solver

**Visualization Options**:
- **Axes**: Blue (X), Green (Y), Red (Z) coordinate system
- **Cube**: 3D wireframe cube with colored faces

### 4. Head Pose Estimation
**Location**: `head_Pose_Estimation/`

Real-time head pose estimation using MediaPipe:

- **`Head_Pose.ipynb`**: Real-time head tracking notebook

**Features**:
- Real-time face detection and landmark tracking
- 6-point facial landmark detection for pose estimation
- Smooth angle calculations to reduce jitter
- Directional head pose classification:
  - Looking Left/Right
  - Looking Up/Down
  - Forward
- Visual feedback with nose projection line
- FPS display for performance monitoring

**Landmarks Used**:
- Nose tip (point 1)
- Left eye corner (point 33)
- Right eye corner (point 263)
- Left mouth corner (point 61)
- Right mouth corner (point 291)
- Chin (point 199)

## 🚀 Getting Started

### Prerequisites

```bash
pip install opencv-python
pip install numpy
pip install mediapipe
pip install jupyter
```

### Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd Camera_Calibrations
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

### Usage Workflow

1. **Camera Calibration**:
   ```bash
   cd Calibartion_Camera_with_checkerboard
   jupyter notebook colabration_checkerboard.ipynb
   ```

2. **Parameter Extraction**:
   ```bash
   cd exract_intrinsic&&extrinsic_parameters
   jupyter notebook EXTRACTING_WITh_checkerboard.ipynb
   ```

3. **3D Pose Estimation**:
   ```bash
   cd 3D_pose-Estimation_camera-cliibration
   jupyter notebook #d_pose.ipynb
   ```

4. **Head Pose Estimation**:
   ```bash
   cd head_Pose_Estimation
   jupyter notebook Head_Pose.ipynb
   ```

## 📊 Technical Details

### Camera Calibration Process

1. **Pattern Generation**: Creates 8x8 checkerboard pattern
2. **Image Capture**: Collects multiple images from different viewpoints
3. **Corner Detection**: Finds chessboard corners with sub-pixel accuracy
4. **Parameter Calculation**: Computes camera matrix and distortion coefficients
5. **Validation**: Saves parameters for use in pose estimation

### Pose Estimation Algorithm

- **PnP Solver**: Uses `cv2.solvePnP()` for pose estimation
- **World Coordinates**: 7x7 checkerboard with 25mm square size
- **Projection**: Projects 3D points to 2D image coordinates
- **Visualization**: Overlays 3D objects on detected checkerboards

### Head Pose Estimation

- **MediaPipe Face Mesh**: 468-point facial landmark detection
- **6-Point Model**: Simplified model using key facial points
- **Angle Calculation**: Euler angles from rotation matrix
- **Smoothing**: Exponential smoothing for stable output

## 🔧 Configuration

### Checkerboard Parameters
- **Pattern Size**: 8x8 (7x7 internal corners)
- **Square Size**: 25mm (adjustable)
- **Image Resolution**: 100 pixels per cm

### Camera Parameters
- **Focal Length**: Calculated from calibration
- **Principal Point**: Image center (default)
- **Distortion Model**: Radial and tangential distortion

## 📝 Notes

- Ensure good lighting conditions for accurate calibration
- Use a flat, rigid checkerboard pattern
- Collect images from various angles and distances
- Avoid motion blur during image capture
- Calibrate camera before using pose estimation features

## 🤝 Contributing

Feel free to submit issues, feature requests, or pull requests to improve this project.

## 📄 License

This project is open source and available under the MIT License.

---

**Note**: This project is designed for educational and research purposes. Ensure you have proper permissions when using cameras and collecting images.
