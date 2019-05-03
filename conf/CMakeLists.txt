# HDE xml files installation
set (HDE_PROJECT_NAME HumanDynamicsEstimation)
set (HDE_XML_FILES xml/TransformServer.xml
                   xml/Human.xml
                   xml/pHRI.xml
                   xml/RobotPosePublisher.xml
                   xml/HumanJointTorquesYarpScope.xml)

install(FILES ${HDE_XML_FILES}
             DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${HDE_PROJECT_NAME}/)

# Install yarpmanager application files
set(HDE_APP_FILES xml/applications/HumanDynamicsEstimation.xml
                  xml/applications/HumanDynamicsEstimation-Human.xml
	          xml/applications/HumanDynamicsEstimation-pHRI.xml
		  xml/applications/HumanDynamicsEstimation-Rviz.xml
	          xml/applications/HumanDynamicsEstimation-TransformServer.xml
		  xml/applications/HumanDynamicsEstimation-YarpScope.xml)

yarp_install(FILES ${HDE_APP_FILES} DESTINATION ${YARP_APPLICATIONS_INSTALL_DIR})

# Install robot urdf files
set(ROBOT_URDF_FILES urdfs/iCubGenova02.urdf
               urdfs/iCubGenova04.urdf
               urdfs/iCubGazeboV2_5.urdf)

yarp_install(FILES ${ROBOT_URDF_FILES}
             DESTINATION ${YARP_CONTEXTS_INSTALL_DIR}/human-dynamic-estimation/urdfs)


# ROS related installation
set (ROS_PROJECT_NAME HDERviz)
set (ROS_PACKAGE_FILE ros/package.xml)
set (ROS_LAUNCH_FILE ros/launch/HDERviz.launch)
set (ROS_RVIZ_FILE ros/rviz/HDERviz.rviz)

# Copy the package.xml, which is necessary to be treated as
# a ROS package
install(FILES ${ROS_PACKAGE_FILE}
             DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${ROS_PROJECT_NAME}/)


# Install the .launch file and the config file
install(FILES ${ROS_LAUNCH_FILE}
             DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${ROS_PROJECT_NAME}/launch/)

install(FILES ${ROS_RVIZ_FILE}
             DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${ROS_PROJECT_NAME}/rviz/)

# Install robot urdf files
install(FILES ${ROBOT_URDF_FILES}
             DESTINATION ${CMAKE_INSTALL_PREFIX}/share/${ROS_PROJECT_NAME}/urdfs/)
