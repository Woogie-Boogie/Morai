# Morai
# -*- coding: utf-8 -*-
Morai Simulation

Morai Simulation 교육 중
- 윈도우 10, wsl과 xlaunch를 사용한 Ubuntu 18.04 환경

[Morai Simulation 설치 및 실행]
1.	catkin_ws_src.zip 파일을 다운 받으시고, 파일을 C:에다가 바로 복사한 후, 
2.	Windows terminal에서 아래 명령을 입력
3.	cd ~/catkin_ws/
4.	rm -rf *
5.	cp /mnt/c/catkin_ws_src.zip ~/catkin_ws
6.	unzip catkin_ws_src.zip
7.	cd ~/catkin_ws
8.	catkin_make

https://morai-sim-for-wego-help.scrollhelp.site/user-manual/%EC%84%A4%EC%B9%98-%EB%B0%8F-%EC%8B%A4%ED%96%89.72909378.html(Morai_launcher_window 다운로드)
v4.4.210806.H2 버전을 설치

아이디 및 비번 kmu0117 / kmu0117

[세이브 파일 덮어쓰기]
첨부된 세이브 파일을 Morai 시뮬 런쳐 폴더에 덮어 씌우기
Sensor와 Network json 파일을 VS code로 열어 Rosbridge IP 를 자기 아이피로 모두 대체해야 함

09. roslaunch rosbridge_server rosbridge_websocket.launch
실행 후, Morai 시뮬 실행하고 차 및 맵을 선택 후 들어가면  9개의 클라이언트가 됨 
TF2Publisher 해제, Disconnect 후 Connect 하면 8개의 클라이언트가 됨


[예제]

10. rostopic list
명령할 수 있는 명령어를 보여준다.

11. rostopic pub -r 5 /commands/servo/position std_msgs/Float64 "data: 0.0"
왼쪽으로 바퀴 방향을 튼다.

11. rostopic pub -r 5 /commands/servo/position std_msgs/Float64 "data: 1.0"
오른쪽으로 바퀴 방향을 튼다.

12. rostopic pub -r 5 /commands/motor/speed std_msgs/Float64 "data: 2000.0"
오른쪽 앞으로 회전한다.

12. rostopic pub -r 5 /commands/motor/speed std_msgs/Float64 "data: -2000.0"
오른쪽 뒤로 회전한다.

[차량 이동]
13. roslaunch racecar teleop.launch
14. rostopic pub -r 5 /high_level/ackermann_cmd_mux/input/nav_0 
탭 3번 입력 -> steering_angle : 0.34, speed : 0.5 설정(speed는 mps)

[rviz]
1. rviz
(1번 터미널 $ roslaunch rosbridger_server rosbridge_websocket.launch
2번 터미널 $ roslaunch racecar teleop.launch
3번 터미널 $ rviz)
-topic : velodyne으로, 
-topic의 image add
-laser scan add, topic, style points 바꾸기

[차량 자세]
1. rostopic echo /imu

[코드 뜯어보기]
1. roscd lane_detection/launch
2. rosed lane_detection steering_publisher.py
3. rosed lane_detection steering_publisher.py
4. roslaunch lane_detection one_lane.launch

5. rosed lane_detection control_wecar.py

