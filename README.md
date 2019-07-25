# The Illusion of The Thinking Machine
This project mixes robot Baxter with a kind of artistic performance to tell a story.

The Illusion of a Thinking Machine

##  Summary
baxter_illusion is a node that makes the baxter performs a sequences of actions with funny face images on the screen, which seems like baxter is live. It would be more interesting if you can pretend to talk and interact with baxter when baxter performs the specific actions.

##  Quickstart
1. Connect your computer to the baxter
2. Put this demo folder my_baxter in $YOUR_BAXTER_WORKSPACE/src the ( $YOUR_BAXTER_WORKSPACE means the path of your baxter_workspace)
3. Change the path of face_images in four files:
	face_stage0.py
	face_stage1.py
	face_stage2.py
	face_stage3.py

	For example, open the face_stage0, find and replace all $YOUR_BAXTER_WORKSPACE with the path of your baxter_workspace, the path may looks like "/home/#your_name#/ros/baxter_ws/BaxterFace/...".

	Do this for all four files
4. To make the baxter go to original position:
	$ rosrun my_baxter face_stage0.py  # make the face go origin
	$ rosrun baxter_examples joint_position_file_playback.py –f $YOUR_BAXTER_WORKSPACE/src/my_baxter/arm_stage0  # make two arms go origin
5. To make baxter ready to move:
	$ roslaunch my_baxter preload_head_face.launch
	$ rosrun my_baxter manager.py
	$ rosrun my_baxter arm_stage1.py
	$ rosrun my_baxter arm_stage2.py
	$ rosrun my_baxter arm_stage3.py
6. To make baxter perform each stage one by one manually:
	In arm_stage1.py terminal window, press enter to run stage1.
	When stage1 end, in arm_stage2.py terminal window, press enter to run stage2.
	When stage2 end, in arm_stage3.py terminal window, press enter to run stage3.

##  Overview
In order to make face, head and arm work logically and synchronously, the node manager.py publishes one message to one topic to make each arm_stageX.py node start up, then arm_stageX.py publishes two messages to two topics to make head and face run immediatelly. In every stage, actions of baxter are designed to make baxter seems like lively. The manager.py node let user press enter to activate every stage in right time.

##  Structure
When launch preload_head_face.launch, 6 nodes of 3 stages starts up:
	face_stage1.py
	face_stage2.py
	face_stage3.py
	head_stage1.py
	head_stage2.py
	head_stage3.py
There nodes did nothing until you press enter in the corresponding 3 nodes:
	arm_stage1.py
	arm_stage2.py
	arm_stage3.py
For example, when press enter to run stage1, arm_stage1.py starts up and publishes messages to make face_stage1.py and head_stage1.py start.

##  Video
	Go to YouTube:
		https://youtu.be/M7LZVu7T7VQ
	Go to qqVideo:


