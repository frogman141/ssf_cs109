# Lab3: Proability, Frequetist, and Statistics

- **Probability** how likely something is going to happen? 
    ```
        probability of an event occuring = number of ways it an event can occur / total number of possible outcomes
    ```
     - There are many ways of thinking about probability:
        - Symmetry of Outcome (Ratios of Outcomes)
        - Relative Frequency of Occurrence 

    - **Key Probability Functions:**
        - **relative frequency:** if there are multiple ways an event like the tossing of a coin can happen, lets look at multiple trials of the event and see the fraction of times one or other of these ways happened
        - **Probability Mass Function:** is a function that maps the proability from values to probabilities.
        - **Cumulative Distribution Function:** is the function that maps from a value to its percentile rank. A function whose value is the probability that a corresponding continous random variable has a probability <= to the arguement of the function.
        - **Probability Density:** A quantity that can be integrated over a range of values to yield a probability. If the values are in units of cm, for example, probability density is in units of probability per cm.
        - **Probability Density Function:** The derivative of a continuous CDF, a function that maps a value to its probability density. 

    - Typically, however probabilities are estimated through creating a model that can simulate an event. Run the simulation a multitude of times and observe the relative frequency an event occurs.

    - The results from each individual round of simulations will fluctuate from each other becoming much smaller as the number of trials increases. It is from these fluctations give rise to the **Probability Distribution** also known as the **Probability Mass Function**.
        - This is utilizing the **law of large number:** as the number of experiments/simulations increase the ratio of outcomes will converge on the theoritical or excepted ratio of outcomes. 

- **What is Data? The Frequentist Perspective**
    - In Frequentist statistics you view a particular sample or dataset provided as a sample from an existing population
    - **Excepted Value:** is the long-run average value of arepition of an experiment
    - **Maximium Likelihood Estimate** (MLE) is a frequentist technique used to estimate a models parameter.
    - **Sampling Distribution:** a probability distribution of a statistics obtained through a large number of samples drawn from a population. The sampling distribution of a given population is the distribution of frequency of a the range of different outcomes for a statistic of that population.

