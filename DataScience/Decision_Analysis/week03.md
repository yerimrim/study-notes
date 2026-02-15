### Decision Making Under Certainty

- Probability: Relative Frequency (by experiment), Subjective Probability (by opinion), Theoretical Probability (by formula)
- **Theoretical Probability**
    1. Probability of Simple Event
        1. $P(A)=\frac{n(A)}{n(S)}$
    2. Probability of One Event or Another Event Occurring
        1. Joint Probability
            1. Independent: $P(A\cap B)=P(A)P(B)$
            2. Dependent: $P(A\bigcap B)=P(A)P(B|A) = P(B)P(A|B)$
        2. Union Probability
            1. Independent: $P(A\bigcup B)= P(A)+P(B)$
            2. Dependent: $P(A\bigcup B)=P(A)+P(B)-P(A\bigcap B)$

- **Conditional Probability**
    - Two conditioned events
        - $P(B|A) = \frac{P(A|B)P(B)}{P(A)}$
    - Multiple conditioned events
        - $P(B_n|A)=\frac{P(A|B_n)P(B_n)}{\sum P(A|B_n)P(B_n)}$

- **Model used for decision-making under risk condition**
    - EV/EMV (Expected Value) ⇒ Choose the highest one
        - $E(X)=\sum p_iX_i$
        - Choose the Alternative which has the Highest value
    - EOL (Expected Opportunity Loss) ⇒ Choose the lowest one
        1. (the highest value in each $p$) - (value in each $p)$
        2. Calculate $E(X)$ in each Alternative and Choose the lowest one
    - EVPI (Expected Value of Perfect Information)
        - EVwPI = $\sum p_i \times$(the **highest** value in each $p$)
        - EVwoPI = the **highest** among each $E(X)$
        - EVPI = EVwPI - EVwoPI
