# Scan Matching Localization
## Project overview
In this final project your goal will be to localize a car driving in simulation for at least 170m from the starting position and never exceeding a distance pose error of 1.2m. The simulation car is equipped with a lidar, provided by the simulator at regular intervals are lidar scans. There is also a point cloud map map.pcd already available, and by using point registration matching between the map and scans localization for the car can be accomplished. This point cloud map has been extracted from the CARLA simulator.

## Setup
Udacity's virtual machine for this project

### 1. Compile the code (Terminal Tab 1)
```
cd /home/workspace/c3-project
cmake .
make
```
### 2. Launch the simulator in a new terminal tab (Terminal Tab 2)
```
su - student
cd /home/workspace
./run-carla.sh
```
### 3. Run the project code back in the first tab (Terminal Tab 1)
```
cd /home/workspace/
./cloud_loc
```

## Requirement
In a drive of at least 170m in the simulator, the pose error never goes above 1.2m.

Be able to continuously localize the car when it is moving at medium speed. In the workspace that is 3 taps on the up arrow. The car shouldn’t have to be moving at really slow speed in order to localize.

### Step 1: Filter scan using voxel filter
The first step is fairly short - make use of cloudFiltered and scanCloud to filter the point cloud using a voxel grid.

### Step 2: Find pose transform by using ICP or NDT matching
The second step is the main portion of the exercise. Finding the pose transformation can be done using either ICP or NDT matching. It is advised to keep the code for this in the main() function as short as possible and instead call out to a different function you create either elsewhere in c3-main.cpp or in a different.cpp file. Also keep in mind that if your ICP or NDT function outputs a 4D transform matrix, you can use the getPose() function in helper.cpp to obtain the Pose object.

### Step 3: Transform the scan so it aligns with ego's actual pose and render that scan
In the final major step, you should be able to transform the filtered scan using your calculated transform into a new point cloud using pcl.

## Result

<img width="960" alt="result_1" src="https://user-images.githubusercontent.com/36104217/179542178-ff762e4f-6ab0-4a48-96f8-890b9bbf0af9.png">
<img width="960" alt="result_2" src="https://user-images.githubusercontent.com/36104217/179542185-ea3e30b8-625d-47c2-a48c-45aa8efb4e44.png">

#Improvement
As suggested, the vehicle moves at a medium speed to keep the maximum pose error below 1.2m, but with medium speed, it would take really long time to reach 170m of travel distance.
In main loop, the Lidar configuration can be changed such as: upper/lower FOV, number of channels, scan range, rotation freqency or number of points per second.
