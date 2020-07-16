# Minimizing-the-cost-of-power-consumption-in-the-data-center
We will leverage an AI solution based on Deep Q-learning to minimize the energy consumption of a single server, and thanks to the object-oriented structure of our implementation, our AI model will be applicable to any server of the same data center, thus minimizing the costs of the whole data center. The solution can be applied and used in the problems of cost minimization for any business related to the data center. So minimizing the energy consumption in the data center will minimize the cost. Thus, tech companies have tremendous costs coming from their data center, and these costs come directly from energy consumption and the different services. This is a special case study but the whole framework that we're going to build is totally adaptable to any other business.<br/> 
To solve this issue we gonna use Deep Q_Learning or DQN as an AI solution. Deep Q-Learning is the model that build by the top of the AI research lab which is a deep mind. Thus, we will give the general framework of how to build an AI with deep Q_Learning and to accomplish a certain goal which is here to minimize the costs. So if you want to apply what we're going to do to your business or your work, you will only have to change a few parameters and a few lines of code to defined differently the different components of the environment such as how you define the reward.<br/>
The server can host the users through the login operation, and also transmit the data in. That increases the temperature of the server. Also, the users can logout from the server and the data could be transmitted out of the server. Hence, the temperature of the server can change, but based on the integrated cooling system the temperature of the server should remain between 18-24 degrees.<br/> 
To define the evnironment we need to set the parametrs and variables<br/>
#### As for parameters: Parameters:<br/>
- the average atmospheric temperature over a month
- the optimal range of temperatures of the server, which will be [18C; 24C]
- the minimum temperature of the server below which it fails to operate, which will be -20C
- the maximum temperature of the server above which it fails to operate, which will be 80C
- the minimum number of users in the server, which will be 10 (**this value is just for simulation purpose**)
- the maximum number of users in the server, which will be 100 (**this value is just for simulation purpose**)
- the maximum number of users in the server that can go up or down per minute, which will be 5
- the minimum rate of data transmission in the server, which will be 20 (**this value is just for simulation purpose**)
- the maximum rate of data transmission in the server, which will be 300 (**this value is just for simulation purpose**)
- the maximum rate of data transmission that can go up or down per minute, which will be 10<br/>
#### As for Variables:<br/>
- the temperature of the server at any minute
- the number of users in the server at any minute
- the rate of data transmission at any minute
- the energy spent by the AI onto the server (to cool it down or heat it up) at any minute
- the energy spent by the server’s integrated cooling system that automatically brings the server’s temperature back to the optimal range whenever the server’s temperature goes outside this optimal range
#### Define the Environment --> State, Reward, and Action <br/>
The ***state*** will be the input of the neural network. The status features are 
- The temperature of the server at time t.
- The number of users in the server at time t.
- The rate of data transmission in the server at time t.
So those elements will be in vector with 3 elements which will be the input of the network. 

The ***action*** that taken is related to heat up or cool down in order to regulate the temperature of the server. <br/>
0 The AI cools down the server by 3C <br/>
1 The AI cools down the server by 1,5C <br/>
2 The AI does not transfer any heat to the server (no temperature change) <br/>
3 The AI heats up the server by 1,5C <br/>
4 The AI heats up the server by 3C <br/>

The ***reward*** is the difference between the energy consumed when we don't have an AI system to regulate the temperature and with an AI system. Now we have one assumption says that the energy spent by the cooling and heating system is the difference between the temperature within time.   
