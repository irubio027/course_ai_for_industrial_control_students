# Lunar Lander Reinforcement Learning Tutorial - Evaluation Questionnaire

- **Grupo:** ________________________________
- **Nombres:** ________________________________
- **Uso de IA: no / sí, para…** ________________________________

Criterio de corrección:se valora sobre todo que entendáis los conceptos y los expliquéis con vuestras palabras y vuestros resultados.

Entrega el cuestionario en formato `.md`, no PDF.

## Student Information
- **Date**: ________________________________
- **Course**: Applications of AI for Industrial Control
- **Tutorial**: Deep Q-Network (DQN) for Lunar Lander

---

## Section 1: Environment Understanding

### 1.1 Task Definition

**Question 1**: What is the goal of the Lunar Lander reinforcement learning task?
- a) Reach the highest altitude possible
- b) Land the spacecraft safely while minimizing fuel consumption
- c) Collect as many points as possible by staying in the air
- d) Crash the lander as quickly as possible

**Question 2**: Complete the Lunar Lander environment specifications:
- **State space size**: ________________________________ (number of continuous values)
- **Action space size**: ________________________________ (number of discrete actions)
- **Landing reward**: ________________________________
- **Crash penalty**: ________________________________

### 1.2 Environment Details

**Question 3**: What do the 4 discrete actions represent in the Lunar Lander environment?
- Action 0: ________________________________
- Action 1: ________________________________
- Action 2: ________________________________
- Action 3: ________________________________

**Question 4**: List at least 5 components of the 8-dimensional state vector:
1. ________________________________
2. ________________________________
3. ________________________________
4. ________________________________
5. ________________________________

---

## Section 2: Deep Q-Network (DQN) Architecture

### 2.1 Architecture Design

**Question 5**: Why is a neural network used instead of a Q-table in the Lunar Lander problem?

_Your answer:_
_______________________________________________________________________________
_______________________________________________________________________________

**Question 6**: What is the purpose of the target network in DQN?
- a) To speed up training
- b) To reduce correlation between Q-value updates and targets
- c) To increase exploration
- d) To reduce memory usage

### 2.2 Network Structure

**Question 7**: In the DQN implementation of this notebook (see the printed `DQN(...)` summary), what architecture is used? How many trainable parameters does it have?
- Input layer size: ________________________________
- Hidden layers: ________________________________
- Output layer size: ________________________________
- Total parameters: ________________________________

**Question 8**: What activation function is used in the hidden layers of the DQN, and why?

_Activation function:_ ________________________________

_Reason (compare with the action counts printed by `analyze_agent_behavior`):_ _______________________________________________________________________________
## Section 3: Training Components

### 3.1 Experience Replay

**Question 9**: Explain the purpose and benefits of Experience Replay in DQN training:

_Purpose:_
_______________________________________________________________________________

_Benefits (list at least 2):_
1. ________________________________
2. ________________________________

**Question 10**: What happens during each training step of the DQN algorithm?

List the 4 main steps in order:
1. ________________________________
2. ________________________________
3. ________________________________
4. ________________________________

### 3.2 Loss Function and Updates

**Question 11**: Complete the loss function used in this notebook:

Loss = Huber (smooth L1)(________________________________, ________________________________)

Where the (Double DQN) target is calculated as:
Target = r + γ × (1 − terminated) × ________________________________

Why does the notebook use the Huber loss and gradient clipping (`clip_grad_norm_`, max norm 10) instead of a plain MSE?

_Your answer:_
_______________________________________________________________________________

**Question 12**: Why is the target network updated less frequently than the main Q-network?

_Your answer:_
_______________________________________________________________________________

---

## Section 4: Hyperparameters and Advanced Concepts

### 4.1 Hyperparameter Analysis

**Question 13**: Match the hyperparameter with its typical value and purpose:

- Learning rate (α): _______ → Controls _________________
- Discount factor (γ): _______ → Controls _________________
- Batch size: _______ → Controls _________________

**Question 14**: Describe the epsilon-greedy strategy used in DQN training:

_Strategy:_
_______________________________________________________________________________

_Why does epsilon decay over time?_
_______________________________________________________________________________

**Question 15**: What does it mean when the Lunar Lander environment is "solved"?

_Criterion:_ _______________________________________________________________________________

### 4.2 Advanced Analysis

**Question 16**: The agent of this notebook uses Double DQN by default (`double=True`). What is the main improvement that Double DQN provides over standard DQN? Which network *chooses* the next action and which one *evaluates* it?

_Your answer:_
_______________________________________________________________________________

**Question 17**: During performance analysis, which action would you expect a well-trained agent to use most frequently, and why?

_Most frequent action:_ ________________________________

_Reason (compare with the action counts printed by `analyze_agent_behavior`):_ _______________________________________________________________________________

---

## Section 5: Your Results vs. the Pre-trained Network

**Question 18**: Fill in the table with the results of **your** run (cells *Training* and *Testing*):

| | Your network | Pre-trained network |
|---|---|---|
| Training episodes / time | ______ / ______ s | (given) |
| Mean test score (10 episodes) | ______ | ______ |
| Success rate (score ≥ 200) | ______ | ______ |

Describe the *BEFORE* (random agent) and *AFTER* animations in one or two sentences each. What does the trained lander do differently?

_Your answer:_
_______________________________________________________________________________

**Question 19**: The replay buffer stores `terminated` (crash or landing) as the end of the episode, but **not** `truncated` (time limit of 1000 steps). Why would it be wrong to treat a time-out as a terminal state in the target?

_Your answer:_
_______________________________________________________________________________

**Question 20**: During training the notebook prints both the "Avg Score (100)" (with exploration) and a periodic "Greedy eval" (ε = 0), and keeps the best network found. Why can the two numbers differ so much, and why is it useful to keep the best network instead of the last one?

_Your answer:_
_______________________________________________________________________________

**Question 21**: Use the *Try it yourself* cell (`pilot(...)`) with several seeds. Find a seed where an agent lands badly (or crashes) and explain what you think went wrong (initial push, terrain, angle…).

_Seed and agent:_ ________________________________

_Explanation:_ _______________________________________________________________________________

