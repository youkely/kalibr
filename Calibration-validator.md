The validation tool extracts calibration targets on ROS image streams and displays the image overlaid with the reprojections of the extracted corners. Further the reprojection error statistics are calculated and displayed for mono and inter-camera reprojection errors.

The tool must be provided with a camera-system calibration file and a configuration for the calibration target. The output YAML of the multi-camera calibrator can be used as the camera-system configuration.

### Usage:

#### Basic online validation

> kalibr_camera_validator --cam camchain.yaml --target target.yaml

#### Validation from rosbag

> kalibr_camera_validator --cam camchain.yaml --target target.yaml --save --input-bag data.bag

#### Several parameters:

> --save

to save the results

> --input-bag

use rosbag file as input validation dataset instead of live image stream

> --cam-error-thres

threshold for mono camera reprojection error to yield a good validation, default = 0.3

> --rig-error-thres

threshold for camera rig reprojection error to yield a good validation, default = 0.5

> --errer-thres-yaml

threshold for reprojection error to yield a good validation, in the file should contain: *{camErrorTol: 0.3, rigErrorTol: 0.5}*

### The output

The validation will produce the following output:

- **%CALIBRATIONNAME%-validation-result.pdf**: Report in PDF format. Contains all plots for documentation.
- **%CALIBRATIONNAME%-validation-result.txt**: Result summary as a text file.
- Corner coverage for each camera is shown on terminal window as an indicator of whether the data is enough for validator