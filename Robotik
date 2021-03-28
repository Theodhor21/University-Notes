## 1-MIddeware: Abstroction layer between os and app layer which simplyfes development & lets ->heterogenus hardware
- Tasks:Comunicat(entites),Computation(task),Config(robotsystesm),Cordination(architectul.system)
- Characteristics of middwar: 1)Hardwar.abstraction,2)Scalibility&Extentibilty,3)LimtOverhead(efficent),4)AccuatorControlModel(drive,motors),5)common chareterstics for the software,6)Tools&Methods(Debug..),7)documentation(usage)
- Framework_fawks:Re use existing modules,develop software from produc tparts, re use sotware ,maintain& costumase part of software to product new function.
- Building blocks:comopnent arrch, module library syst arch,framework ,
- Fawkfaturers:1Oriented prog, 2welld defin compnent, r3untaime loadbable in Plugin mechanismus, 3plugin as threads impl , multithreaded,Aspectorientated framework,Strudturred and synchron in main loop.
- ROS:Open source ,Diff os supp,Standart ,
- ideaRos: peer-peer,Multi language,Toolboxes(unixcomadn)
- RosTerminoligy:Packages(fucntion entity core),Manifasto(Cmake package ifno),Stack,Msg, servicetypes.
- Nodes:comp enityt usr rso library,Functiony encapsuled
- Master:conects peers stores topics, orginases noe graph structur for nodes  to comunicate
- Parameter server: Stores data under specifc key.
- Bags:Data contaienr to store rundata which can be repaly
- ros2:Real time supp, data distributiion service  quality,multiple oss supp
- service:like sub puib but blockng req resp
- Action: For long runing tasks behaviours

## 2-Sensor
- wheel encoder:rev time 
- gyroskop,Accelmoeter,IMU:
- TimeofFlight: ref and back
- Proprotivevs Extracaptive sensor: inner outer state
- Aktive vs Pasiv: emit smtnin or no  
- Type of errors:
  - Systematic errors: Factors and proceses describeble by theoretic model (robot 1  m vor finish) lense easy to  fix
  - RandomErros:Not describable by model need statistic model sensor nosie in radar 
  - Precison: Standart devation distributon of error signal we can calcuate a solutuion for sensor pricisnes
  
## 3 Kinematics:
### Manipulaion vs Locomotion:
#### LegsvsWheels:
- Pose: Robot consist of rigidbodys conectetd by joints Pose describes positon and orientation in space.
- Kineatics: Describe Poses,Speeds,acceleration of Rigidbodys:
- Dynamics:force&Torque.
- Differential Drive: Translation & rotation. then comes 
- Discrate state equation: xt+1=xt+∆vt*cos ot|yt+1=ty+∆v* sin ot and ot+1: ot +∆t
- Range data in polarcord:x=rcosa y=rsin a
- rotation of cathesian coordiates: X=xcosa-ysina Y=xsina + yCosa
- Rotation matrix: r(Z,alf),.. rotate a vector or a oreinatation(is rotation amtrix too)
- rotation in space euler: Yaw pitch roll Z Y X  Need to transfor in Roation matrix then we do the Ratiations or quaternions  acordint to y x z which icauses roation matrix has  Singularities for pitch=pi/2 (divisen b 0 )
- Quaternionos: Analogy to complex nr(only rotation)
- Homogens Cordinaton Tranform matix: extend with a 4th dimensioon to do translation and rotation in one step.
- Kinamtic xchain: From joint to join transformation(using homogen transform matrix) to find pose:
- FowardKinemtaics: Computate Pose from joint angels 
- ReversKinamtics:computate Joint anges when given a pose (hard) only in smoll cases calcuatet most used numerical methods such as gradient ways

## 4-Local Navigation:
-Potntialfields:qstart to q goal.  goal attracts obsticle repell
- Do gradient of Potentil field to get Vector force->ForceField.
- HesseMatrix:second derviate to find max min or sattle point.
- Attractv incires if we away from goal. repllent if we close to ovsticle..
- GradinetDescent Alg:Compute grad all poitns q0..qn go thru these points while grad(q)=!0 we go to the direction of steapest discent untill we reach 0 
- Implenetetd thru bushfire alg: Local map where we compute the repelletn forces around obsticales and filll all map 
- Probles of bushfire: LOCAL MINIMA: concave-> grad 0 stops us
- Avoiding local minima:Presentspace in 2d grid wher begin all 0 set target 2 and incise with 1 each neighbouring box till we fill grid 
- Examples:1)Roadmaps:First shortes parth,2)Visibilty graph:uses tringaltuions to fidn the path and asing road,3)Varnoi diagram:calcuates max distant to obsticla. 4)Canny rodalg: Uses edge detectuion to scan osticals. put target at end of visibilty
- How to realise motion comand:1)Advoidance path planing
 - 2) Dynamic obsticle caousese new local target poitns
- Problems->Robotz will not reach point cant distingush target..
- Actions->Switch Points,useSmooht velocit controller,useHysteria function for stabilty
- PID CONTROLLER::We have goal A_goal but we are at A_now. So we calculate the error=A_goal-A_now and use it to calculate an input.
  - Proportional Gain: Input = P * error
  - Integral Gain: Input = P_I * sum(err) -use acumulated error
  - Derivativ Gain: Input = P_D * (err -err_prev) - use change in error
  
  
 ## 5-PathPlaning:We need start goal edge weights strategyInitalstate:S0TransitanModel:goin(aachen)=Saachen
- SpaceState:Initalstate and actions
- Path: Start to goal  .optimalsolutin: Cheapest path
- SearchTree Rutplaning:
- Loop( if fronter=0 then finish, expeand in leaf remove from frontier if node = goal end
- We need perent to track our tree. and use QUEUES for frontier.
- UnInformedSearch:
- 1)BFS(Breadthfirst):FIFo frontier one lvl first  compexity bfuqid and space bfuqid keeps nodes in memory expnentail growth
- Alg BFS:if frontier eamtpy ->false else pop from forntier node adde node to explored and explare all chirdlre put fornter if its not in the explored list till we reach our goal solution
- Problems bfs:expxontal growth paths have same coast.
- 2)UCS(Unform Cost Search): Same as bfs but uses prio que for foritner. sow we take smallst path first can be same as exonentail as bfs.
- 3)DFS: Deapth first searxch:Foritner but in LIFO queue so we explor till the end. complexity (bfuqim) space (b*m)
- Problems: Can go to inifinity unlimitd deapth: thats why Deaptth limited searchset limitd deapth   ore iterative depath search incremant the deapth limit as we wish.
- Compelte:BFS UCS IDS,
- Optimal:Bfs,ucs
- HEUROSIT SEARCH(Informed search): h(n)= extemated cost of cheapest path to n  cost is f(n)=g(n)actual csot+h(n)
- A* SEARCH:Optiaml and complete identical to ucs but use astemated cost.
- Optimaluy for A*:to be optimal the heursitc function must be optimal and not overestiamte coast very impornat for our alg and complecity.
- A* for grids: Same as tree but we have Grids neihgobuts in which we expand 
- THe meanint of heruosut function to huge so we dont run out of memory branching
- Propabalstic Roadmaps:large spaces cant do deterministic search -> probalistc road maps we generate random samples finde neighbor relationshpis between them and do a path findg alg to this ponits.
- Nevigatio search in ros: We combine kinematics local nav and paht planing.
 - we Do global planing in local bases on the semsor and the dynamic of the world
 
 
## 6-Localisation:
a. Terms:
Conditional probability: p(A|B) - propability of A given b
Joint probablity: p(A,B)- propability of A and B.   p(A,B) = p(A|B) * P(B) = p(B|A) * P(A)
Independence: P(A|B) = P(A) so  p(A,B) = P(A) * P(B)
Bayes rule: Transforming conditaional probabs for ex: given p(A|B) ->  p(B|A) = p(A|B) *P(B) / P(A)
Gaußian(uniform) distribution: bell form distribution with mean and varianc
Markov chain: assumtuion that our state depends only on the previoust state and no state before that

b.  Localization
Idea: Estimate the state distribution (with a belief) given previous states, inputs and meassurments
         -> markov chain simplification:  given previou state, input and meassurment at this timestep
Using Bayes Filters: motivated from markov chain and baysan rule we estimate the belif using a motion modol and a messurement model 
Setp1)Preditction Step given prev belif predict the new belif using motion model
step2)corrction step use messurments and messurment model to correct the belif

## 6.1-GridLocalisation: aprox belif discretly using a histogram like grid over the state space
1- initialise all cells with weight 1/n
2-every step 
- use use motion model and messurmant model to update the weights of the cells


Estimate the position: 
1-weighted summ of the centers of the cells
2-postion of cell with max weight

problems:
1.Qualtiy depnes on nr of cells, but compelxti increases with nr of cells -compared to Kalman Filter
2. We keep updating all cells althought mayn wrong no resampleing -- compared to Monte Carlo
Advantage: multimodal ( global localization, kidnapped robot)

Instances of bayes filters ---------------------------------------------------->

## 6.2-Montecarlo(particleFilter):Uses n samples where each has positon and Weight
1-Initialize samples with 1/n and postion randomly
2-each step 
- Prediction: we use motion model to udpate positon of all samples a
- Correction: we use measurment model to udpate weights of all steps
-Resampling:sample with replacment of the samples.Idea:Allow the sampls with big weights to survive so we dont have to keep track of samples with very small weights.

problems:
1.Qualtiy depnes on nr of samples, but compelxti increases with nr of samples -compared to Kalman Advantage: 
1-multimodal ( global localization, kidnapped robot)
2- resampling: efficient

## 6.3-KalmanFilter: use gaussian distribution for the belif
Prob Motion Model: Motion Model + Gaussian Noise
Prob Measurment Model: Meas Model + Gaussian Noise
(Noise with 0 mean to make up for inaccuracies)

Belief should be initialized in the beginning
In each step:
1- Prediction step: use probalistic motian modal to update belif(mean and varianc)
2-Correction step: use probalistc massurmant model to correct the belif (our mean and varianc)

Problems: monomodal( bad for global positioning, bad when kidnapped)
Advantages: robust, very fast
--------------------------------------------------------------
 Mapping:
- Similiar to localiztion  but we are given position and want to estimate the position of all landmarks
- Use inverse measurement model
Interesting fact: There are arlgorithmes called slam that build map and localize simultanously
