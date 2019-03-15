## Flappy Bird with Q-Learning
A simple implementation to [Playing Atari with Deep Reinforcement Learning](https://www.cs.toronto.edu/~vmnih/docs/dqn.pdf).\
Train your bird at [https://wentaocn.github.io/q-bird](https://wentaocn.github.io/q-bird).

![score-10000](chart/score-10000.png)

### How it works
```
Q ← {}
state-seq ← []

for each round:
    for each frame:
        S ← current state
        if S in Q:
            if Q(S, flap) > Q(S, do-nothing):
                A ← flap
            else:
                A ← do-nothing
        state-seq ← state-seq + [S, A]

        if terminal:
            for [S, A] in reversed(state-seq):
                if S is the 1st (closest to terminal):
                    Q(S, A) ← (1 - α) * Q(S, A) + α * R
                else:
                    S' ← next state of S
                    Q(S, A) ← (1 - α) * Q(S, A) + α * {R + γ * max[Q(S', flap), Q(S', do-nothing)]}
            state-seq ← []

α: learning rate
γ: discount factor
R: reward
       +1 for survival
    -1000 for death
```

### Result: after 1000 rounds' iteration
<img src="chart/chart-0.png" alt="drawing" width="45%"/> <img src="chart/chart-1.png" alt="drawing" width="45%"/>

<img src="chart/chart-2.png" alt="drawing" width="45%"/> <img src="chart/chart-3.png" alt="drawing" width="45%"/>

### Credits
[https://github.com/enhuiz/flappybird-ql](https://github.com/enhuiz/flappybird-ql)\
[https://github.com/chncyhn/flappybird-qlearning-bot](https://github.com/chncyhn/flappybird-qlearning-bot)
