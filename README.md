# SelfishKuramoto
A small simulation project exploring what happens when oscillators in a Kuramoto network are allowed to choose their own coupling strength using reinforcement learning (REINFORCE).

## Model
$$\dot\theta_i = \omega_i + \frac{K_i}{k_i}\sum_j A_{ij}\sin(\theta_j-\theta_i)$$

- NETWORK: $00 oscillators arranges in a Watts-Strogatz small-world graph (k=10, p=0.1)
- Each oscillator i learns its own preferred coupling strength $\mu_i$
- Oscillators get rewarded for staying aligned with their local neighbors, but paying attention costs energy( $c\cdot K_i$).


## OBSERVATIONS
- At c=0.05, when every oscillator starts out of sync trying to couple is pointless so everyone drops their $K_i$ to zero. And if they all start synced they stay synced
- When cost becomes too high even when oscillators start in sync, agents slowly lower their coupling to save cost until the whole group suddenly collapses into chaos
- When synced, oscillators whose natural frequencies ($\omega$) are close to the mean drop their coupling near zero and coast. Fast and slow outliers have to pay a high coupling cost to stay locked in, forming a clear V-shaped when plotting learned $K_i$, against $\omega$

![Uploading image.png…]()
