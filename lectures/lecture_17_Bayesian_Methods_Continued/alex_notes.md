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
            3. Ovserve the result of pulling bandit B, and update your prior
            4. Return to step 1.
        - The bayesian solution does assume the starting priors of winning for each bandit to begin with. Typically, the start assumption is a flat prior.
        - That is at the beginning we assume all probabilities of winning are equally likely. This is called a minimally informative prior.
        - **Bayesian Bandit updating mechanism:**
            - Let our prior parametesr be a and b
            - Let x be the result of pulling on arm (either 0 or 1)
            - Then our posterior parameters are a' = a + x, b' = b + (1 - x)

- **Markov Chain Monte Carlo (MCMC)**
    - 