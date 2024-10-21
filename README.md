# Coppeliasim
1. Problem Statement
In this task, teams have to write code to implement LQR or PID control strategy to balance the bot at its unstable equilibrium point using python child scripts in the given CoppeliaSim scene.

The given bot should be balanced at upright position and should also parallely maintain the position of the bot as shown in the below video

This task should be accomplished using given scene environment without changing simulator or scene object properties. Team can change only the child scripts, following the mentioned guideline.


2. Given
1. CoppeliaSim's Scene File (Task_1B.ttt)
Open the scene file i.e. Task_1B.ttt in CoppeliaSim, you will see the scene as shown in the Figure 1.

Figure 1: Coppeliasim Scene

You’ll find a hierarchical tree structure similar to the one shown in Figure 2.

Figure 2: Scene Hierarchy

The objects in the scene along with their names and uses are given in Table 1.

Name in the scene	Use (s)
bot_body	Acts as inverted pendulum which has to be balanced by moving the wheels
right_joint	As an actuating joint behaving as motor for the right wheel around which the wheel rotate
right_wheel	Acts as the right wheel for the bot
left_joint	As an actuating joint behaving as motor for the left wheel around which the wheel rotate
left_wheel	Acts as the left wheel for the bot
Table1: Objects in the hierarchy
Notes :

In this task, you are NOT allowed to add or remove objects in scene.

Any change in the names of the objects, their parent child relationships, their properties, position, orientation etc. will result in poor evaluation and hence low marks.

Bot's Body is having a mass of 0.05 kg

Right & left wheels are having a mass of 0.018 kg

Right & left motors are revolute joints in velocity mode, with a max.torque rating of (2.5 Nm).

If you’ve followed the Introduction to CoppeliaSim tutorial, then try exploring other options in CoppeliaSim like the position and orientation of object in different frames, etc. You can set a good camera view in simulation for yourself But yeah, make sure you use a fresh scene before starting implementation of the task - to make the evaluation smooth. 👍

2. Understanding the Task:
You’ll find a script icon as shown in Figure 2.

Click on the script icon. You’ll have the script opened as shown in Figure 3. You have to edit this file by writing your code in appropriate function to execute the control loop to balance the bot.

There are explainatory comments given in each function - read them through.


Figure 3: Simulation Script

3. Applying Control Technique (LQR/PID):
You are allowed to use either of LQR or PID control technique to balance the bot.

LQR: 🦾
This desired performance is specified by Q & R matrices. Q is the state cost weight matrix & R is the input cost weight matrix. Both are diagnol matrices.

For Q - each diagonal value corresponds to a state(as per state sequence) and it is of nxn size for n states. Whereas R is of uxu size for n states and u inputs. The diagonal entries of R correspond to each input.

Choosing Q & R is takes a thorough understanding and observation of system dynamics. Weights in Q matrix should be given in a sequence such that higher priority is given to the most critical states for the controller. Similary R matrix shares the energy cost among all the inputs. For single input system it’s less significant as all energy is given to single input only.
The relative values of weights matter for Q & R matrices. The absolute value doesn’t make much change.(Learn more about using lqr() function here)
Refer this to learn more about LQR design.

This is a nice video for developing intuition about LQR

PID :💪
This technique can be applied without knowing state-space model. It requires lesser efforts in math as it’s an observation based tuning method, but there are ways to mathematically tune it for our system for optimal performance.

IMPORTANT NOTE : Learning about PID is NOT compulsory for this task. Teams can use either of PID or LQR for completing this task.

There are good resources on PID tuning like

Proportional-Integral-Derivative Controller - Wikipedia
MATLAB Tech-Talks playlist on PID
Refer this to learn more about PID controller Design
PID Tuning:
Tuning -1
SUGGESTION 📝 : Controlling tilt angle and position may require more than a straightforward PID. So you can try out variations of it. For example, cascade control or parallel PID etc.
