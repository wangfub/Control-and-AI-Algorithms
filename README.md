# Control-and-AI-Algorithms
Implementations of Control (PID, LQ, MPC, ...) and AI (fuzzy logic, Q-learner, SARSA, ...).
The algorithms are briefly discussed in this readme, and some results are shown. For detailed explanation, see the readme's of each project.

Overview:
1. [Fuzzy Logic](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Fuzzy%20Logic)
2. [LQ Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/LQ%20Control)
3. [Model Predictive Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Model%20Predictive%20Control)
4. [PID Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/PID%20Control)
5. [Q-learners and SARSA](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Q-Learning%20and%20SARSA)
6. [System Analysis](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/System%20Analysis)

## 1. [Fuzzy Logic](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Fuzzy%20Logic)

Implementation of Fuzzy Logic in MATLAB. In Fuzzy Logic, the truth values of variables may be any real number between 0 and 1. 
Therefore, it can handle 'partial truth', where the truth value may range between completely true and completely false.

## 2. [LQ Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/LQ%20Control)

LQ control is implemented using Simulink and MATLAB.

First the situation without control. All variables will go towards their equilibrium values.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/noControl.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/noControl.png" width="400">

With LQ control, the controllable variables (k and v) will go towards the desired value. Uncontrollable variables (s) cannot be controlled.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/LQControl.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/LQControl.png" width="400">

Sometimes, some variables cannot be measered directly. An observer will estimate these values.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/noControlObserver.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/noControlObserver.png" width="400">

The observer can be combined with LQ control.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/LQControlObserver.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/LQControlObserver.png" width="400">

Finally, a reduced order observer can be used as well.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/LQControlReducedObserver.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/LQControlReducedOrderObserver.png" width="400">

To achieve optimal control, the controlmatrix can be optimized (on an other system).

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Simulink%20models/optimalLQControl.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/LQ%20Control/Results/optimalControl.png" width="400">

## 3. [Model Predictive Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Model%20Predictive%20Control)

Implementation of MPC on a basic system with the following uncontrolled step response.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/StepResponse.png" width="400">

After optimization of the parameters, the model predictive control algorithm will accurately responds on a change in the set point. Left the response, right the taken control action.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/ControlledSystem.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/ControlAction.png" width="400">

The calculations done by the MPC around the change in stepoint are visualised below:

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/t1003.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/t1020.PNG" width="400">

The impact of the parameters m and p is visualised:

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/VariationM.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Model%20Predictive%20Control/Figures/VariationP.png" width="400">

## 4. [PID Control](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/PID%20Control)
A standard PID controller is implemented in Simulink and MATLAB. The influence of the different control settings is studied.
<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/PIDcontroller_model.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/PIDcontrollerInfluenceP.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/PIDcontrollerInfluenceI.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/PIDcontrollerInfluenceD.png" width="400">

The PID tuning will perform less optimal if their is a measurement delay.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/controlWithMeasurementDelay.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/controlWithMeasurementDelay.png" width="400">

To efficiently tune the system, control margins are plotted on a BODE-plot for a system of respectively first, second and third order.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/marginFirstOrder.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/marginSecondOrder.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/marginThirdOrder.png" width="400">

We will now tune the PID controller. First the state without control.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/PIDTuningNoControl.PNG" width="400">

The open loop response.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/PIDTuningOpenLoop.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/PIDTuningOpenLoop.png" width="400">

And then the calculated optimal PID control.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/PIDTuningControl.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/PIDTuningControl.png" width="400">

Lastly, a PID-feedbackward controller is combined with a feedforward controller. We assume the noise distrubing the system is perfectly characterised. This combination effectively maintains the desire state.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/Simulink%20models/FeedforwardBackward_model.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/PID%20Control/FeedforwardBackward.png" width="400">

## 5. [Q-learners and SARSA](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/Q-Learning%20and%20SARSA)

Q-Learning and SARSA algorithms are used to let an imaginary cat (red) through a maze. Besides not running into the walls, the cat tries to locate the mouse (blue).

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Q-Learning%20and%20SARSA/CatMouse.PNG" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/Q-Learning%20and%20SARSA/CatMouse2.PNG" width="400">

## 6. [System Analysis](https://github.com/WardQ/Control-and-AI-Algorithms/tree/master/System%20Analysis)

Several systems are investigated with Bode and Nyquist plots.

A first order system.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/BodeFirstOrder.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/NyquistFirstOrder.png" width="400">

A second order system.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/BodePole.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/NyquistPole.png" width="400">

A third order system.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/BodeSeries.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/NyquistSeries.png" width="400">

Root locus analysis is performed on these three systems.

<img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/poleAnalysisFirstOrderSystem.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/poleAnalysisSecondOrderSystem.png" width="400"><img src="https://github.com/WardQ/Control-and-AI-Algorithms/blob/master/System%20Analysis/poleAnalysisZPKSystem.png" width="400">
