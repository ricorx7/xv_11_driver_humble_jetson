# XV-11 Driver For Lidar From Neato

This specific version is intended to be used on a Jetson Nano in a docker container that is running ROS2 Humble in Ubuntu 18. 

This is a port from https://github.com/muditguptacode/xv_11_driver_humble.  

This is a port of the popular ROS driver called  xv_11_laser_driver

This is a port so most credit goes to original developers.
Please see ROS version here:  https://github.com/rohbotics/xv_11_laser_driver

Place this repository in your colcon_ws workspace

    cd ~/colcon_ws/src
    git clone <this-repository>
    cd ..
    colcon build

NOTE: when building on a platform with limited resources, the build can get stuck indefinitely, 
to get around that problem use the sequential build parameter as to not overwhelm the system, like so:
    
    colcon build --executor sequential 

Once it has been made and registered by sourcing it to your environment by running:

    source ~/colcon_ws/install/local_setup.bash

you may run it as follows

The following ROS2 parameters are defaulted as below and can be set using parameters

    port              /dev/tty_xv11_driver
    baud_rate         115200
    frame_id          neato_laser
    firmware_version  2

Run the driver and it should generate scan data on topic /scan

    ros2 run xv_11_driver xv_11_driver

Run the driver using a different frame_id

    ros2 run xv_11_driver xv_11_driver --ros-args -p frame_id:=xv11_scan

If all goes well this will produce messages of type LaserScan on topic /scan

    

