# Selfish-Kuramoto
A small simulation project exploring what happens when oscillators in a Kuramoto network are allowed to choose their own coupling strength using reinforcement learning (REINFORCE).

## Model
$$\dot\theta_i = \omega_i + \frac{K_i}{k_i}\sum_j A_{ij}\sin(\theta_j-\theta_i)$$

- NETWORK: 400 oscillators arranges in a Watts-Strogatz small-world graph (k=10, p=0.1)
- Each oscillator i learns its own preferred coupling strength $\mu_i$
- Oscillators get rewarded for staying aligned with their local neighbors, but paying attention costs energy( $c\cdot K_i$).


## OBSERVATIONS
- At c=0.05, when every oscillator starts out of sync trying to couple is pointless so everyone drops their $K_i$ to zero. And if they all start synced they stay synced
- When cost becomes too high even when oscillators start in sync, agents slowly lower their coupling to save cost until the whole group suddenly collapses into chaos
- When synced, oscillators whose natural frequencies ($\omega$) are close to the mean drop their coupling near zero and coast. Fast and slow outliers have to pay a high coupling cost to stay locked in, forming a clear V-shaped when plotting learned $K_i$, against $\omega$


<img width="800" height="500" align="center" alt="image" src="https://github.com/user-attachments/assets/429373f0-05d7-4ee0-9a19-bed1e1c4448f" />

## SAMPLE-ANIMATION
when c=0.02, we observe that with time, the nodes form an arc, while some nodes dont (they dont get coupled), so 
they do their own thing. The arc nodes become full coupled i.e they all have the same phase $\theta$

![GIF](selfish_kuramoto (1).gif)
