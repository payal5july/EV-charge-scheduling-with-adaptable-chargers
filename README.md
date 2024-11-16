# EV-charge-scheduling-with-adaptable-chargers
A Multi-Objective Optimization Framework for Electric Vehicle Charge Scheduling with Adaptable Charging Ports. This paper was published in IEEE Transactions on Vehicular Technology in 2022.

This paper proposes a model for managing an electric vehicle (EV) charging station equipped with adaptable charging ports. A charging station with adaptable ports can provide energy at variable rates, which are adjustable in discrete steps. It emphasizes the following key points:

1. **EV Scheduling and Pricing**: The charging station manages EVs based on their arrival, departure times, and energy requirements. It buys electricity from the grid and sells it to EV owners with a profit margin that depends on the grid's load and charging speed (slow or fast). Incentives (penalties for the station) are provided for unmet demand to encourage customer satisfaction.

2. **User Satisfaction Factors**: EV owner satisfaction is modeled based on three factors: cost, energy received, and time saved (charging completed before the deadline). Customer satisfaction at a charging station depends on three factors: saved time, energy charged, and price paid, with total satisfaction calculated as the product of individual satisfaction components for all customers.

3. **Actions Available to the Charging Station**:  
   - **Charge**: Provide energy at slow or fast rates, earning revenue.  
   - **Wait**: Delay charging due to constraints, paying a penalty for preemption.  
   - **Deny**: Refuse service if scheduling is impossible, paying a higher penalty.  
   - **No Action**: Take no further action once the EV has left or been denied service.  

4. **Grid and Selling Prices**: The cost of electricity from the grid depends on a quadratic function of grid load while selling prices vary based on the charging speed. This ensures profitability while accommodating customer demands.

Overall, the model integrates scheduling, pricing, and satisfaction mechanisms to optimize the charging station's operations while balancing revenue and customer experience. To solve this problem, an SMT-based model (Z3 solver using Python API) is developed for optimal problem-solving, complemented by NSGA-II for handling computational complexity; a heuristic algorithm is proposed to provide near-optimal solutions more efficiently and improve SMT scalability by incorporating heuristic-derived constraints.

The paper also compares the time complexities of the three algorithms. The optimal solution has an exponential complexity of $\mathcal{O}(5^{vH})$, making it impractical for large inputs. NSGA-II is faster with a complexity of $\mathcal{O}(I_{ga}vHN_{ga}^2)$, but remains computationally intensive. The proposed CAR algorithm is significantly faster, requiring $\mathcal{O}(N_hvH + N_h^2)$, which simplifies to $\mathcal{O}(N_h^2)$, making it more efficient and scalable.

