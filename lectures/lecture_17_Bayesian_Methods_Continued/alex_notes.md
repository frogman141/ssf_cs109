# Lecture 17: Bayesian Methods Continue

- **Empircal Bayes**
    - Empircal Bayes methods are procedures for statistical inference in which the prior distribution is estimated from the data. This differs from traditional bayesian methods because you typically decide your priors a head of time.
    - The first step Empircal Bayesian Inference: is to estimate the beta prior using the data you already have.
    - The second step is to use the estimate distribution as a prior for each individual estimate. Then update the distribution based on individual observations.

- **Confidence vs Credibility Interval**
    - **Overview**
        - The differences in confidence vs credible intervals comes from the difference between bayesian and frequintist views of probability.
        - When you compute credibility regrion this region says: given our observed data, there is 95% probability that the true value of model parameter falls within the credibility region
        - Frequentist confidence intervals says: there is a 95% probability that when you compute confidence interval, from data of this sort, the true mean will fall within the confidence intervals
    - **The differences between the 2 types of constraints:**
        - The bayesian appoarch fixes the credible region, and guarntees 95% of possible values of a parameter for a model will fall within.
        - The frequentist appoarch fixes the parameter, and guarntees that 95% of possible confidence will contain it.
    - **Frequentist and Bayesian confirmation the distrinctions come from the theme definitions of probabilities:**
        1. Bayesian treat parameters, as random variables, while frequentist treas parameters as fixed.
        2. Bayesian treats a model parameters constraints as fixed, while frequentists treats a models parameter as a random variable.
    - **Method of calculating a Bayesian Credibility Interval:**
        1. Sample random model parameter values from the prior 
        2. Sample random random sets of point given each model parameter
        3. Select the sets of points which master our observed data.
        4. ask what fraction of these parameter values are within the crebility interval we've constructed.

- **Bayesian Bandit**
    - **The Multi-Arm Bandit Problem**
        - Suppose you are faced with N slot machines (colourfully called multi-armed bandits). Each bandit has an unknown probability of distributing a prize (assume for now the prizes are the same for each bandit, only the probabilities differ). Some bandits are very generous, others not so much. Of course, you don't know what these probabilities are. By only choosing one bandit per round, our task is devise a strategy to maximize our winnings.
    - **Applications of the Multi-Armed Bandit problem:**
        - **Internet display advertising:** companies have a suite of potential ads they can display to visitors, but the company is not sure which ad strategy to follow to maximize sales. This is similar to A/B testing, but has the added advantage of naturally minimizing strategies that do not work (and generalizes to A/B/C/D... strategies)
        - **Ecology:** animals have a finite amount of energy to expend, and following certain behaviours has uncertain rewards. How does the animal maximize its fitness?
        - **Finance:** which stock option gives the highest return, under time-varying return profiles.
        - **Clinical trials:** a researcher would like to find the best treatment, out of many possible treatments, while minimizing losses.
    - **Bandit Algorithms**
        - These are algorithms are designed to solve the bandit problem by determining how to best allocate between competing (alternative) choices in a way that maximizes their expected gain, when each choice's properties are only partially known at the time of allocation,and may become better understood as time passes or by allocating resources to the choice.
        - **Explore vs Exploitation Predicament**
            - This problem is known as explore vs. exploit. Should we “explore” – i.e. try a new machine in hopes that its probability of winning is higher? Or should we “exploit” – i.e. the machine we are using now is pretty good, so let’s keep going?
            - Explore vs Exceptation predicament is essentially, should we continue allocating resources as they are or do we explore for potientially more efficient method of use for your resources.
    - **Thompson Sampling for Bernoulli Bandits (A Bayesian Bandit Algorithm)**
        -  **Algorithm For Each Trail:**
            1. Sample a random variable X, from the prior B, for all B
            2. Select the bandit with the largest sample, i.e. select bandit B = argmax Xb
            3. Observe the result of pulling bandit B, and update your prior
            4. Return to step 1.
        - The bayesian solution does assume the starting priors of winning for each bandit to begin with. Typically, the start assumption is a flat prior.
        - That is at the beginning we assume all probabilities of winning are equally likely. This is called a minimally informative prior.
        - **Bayesian Bandit updating mechanism:**
            - Let our prior parametesr be a and b
            - Let x be the result of pulling on arm (either 0 or 1)
            - Then our posterior parameters are a' = a + x, b' = b + (1 - x)

- **Markov Chain Monte Carlo (MCMC)**
    - **The Bayesian Landscape**
        - When we setup a Bayesian inference problem with **N unknowns**, we are implicitly creating an **N dimensional space** for the prior distributions to exist in. Associated with the space is an additional dimension, which we can describe as the **surface, or curve**, that sits on top of the space, that reflects the **prior probability** of a particular point.
        - If these surfaces describe our **prior distributions** on the unknowns, what happens to our space after we incorporate our observed data **X**? The data **X** does not change the space, but it changes the surface of the space by **pulling and stretching the fabric of the prior surface** to reflect where the true parameters likely live.
        - more data means more pulling and stretching. Less data, and our original shape is more present. Regardless, the resulting surface describes the **posterior distribution**. 
        -  The data essentially **pushes up** the original surface to make **tall mountains**. The tendency of the observed data to **push up** the posterior probability in certain areas is checked by the prior probability distribution, so that less prior probability means more resistance
    - **How to Search the Bayesian Landscape**
        - We cannot naively search the deformed posterior space N-Dimensional because it's fundamentally exponentially difficult. That's why we use MCMC to converge towards the mountains of posterior probability.
        - Converging usually implies moving towards a point in space, but MCMC moves towards a **broader area** in the space and randomly walks in that area, picking up samples from that area
        - MCMC does this by exploring nearby positions and moving into areas with higher probability taking samples as we go along. We take samples in order to take advantage of the **law of large numbers**.
        - **There is a large family of algorithms that perform MCMC. High Level of MCMC follows:**
            1. Start at current position.
            2. Propose moving to a new position (investigate a pebble near you).
            3. Accept/Reject the new position based on the position's adherence to the data and prior distributions (ask if the pebble likely came from the mountain).
            4.  1. If you accept: Move to the new position. Return to Step 1.
                2. Else: Do not move to new position. Return to Step 1. 
            5. After a large number of iterations, return all accepted positions.
        - This algorithm moves in the general direction towards the regions of posterior distributions, and collect samples sparingly on the journey. 
        - Once we reach the posterior distribution, we can easily collect samples as they likely all belong to the posterior distribution. 
        - When the MCMC algorithm position is in an area of extremely low probability, the algorithm will move in positions **that are likely not from the posterior** but better than everything else nearby.