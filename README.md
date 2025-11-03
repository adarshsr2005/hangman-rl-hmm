# hangman-rl-hmm
Hangman AI using HMM and Reinforcement Learning

This project implements an intelligent Hangman-playing agent using:

Hidden Markov Model (HMM) as a language oracle

Q-Learning Reinforcement Learning agent

Candidate word filtering using regular expressions

Epsilon-decay exploration strategy with heuristic fallback

hangman-rl-hmm
 ├─ 01_data/
 │   ├─ corpus.txt        # Training dataset
 │   └─ test.txt          # Testing dataset
 ├─ 02_src/
 │   └─ hangman.ipynb     # Complete code (HMM + RL)
 └─ README.md

 Problem Statement

Develop an AI agent capable of playing the Hangman word-guessing game.
The agent does not know the word; it must learn from experience and language patterns.

Objectives:

Build an HMM to model English letter probabilities

Build an RL agent that learns optimal guessing strategy

Combine both to improve accuracy and performance

Evaluate using the hackathon scoring formula

Final Score =
  (Correct Words × 2000)
- (Wrong Guesses × 5)
- (Repeated Guesses × 2)

 Note: A reward of +10 per correct guess was used only during training to help RL convergence.

 Approach
1. HMM Oracle

The HMM learns the following probability distributions from the training corpus:

Global letter probability

Letter probability conditioned on word length

Letter probability conditioned on both position and length

This provides P(letter | context), guiding the RL agent.
2. Reinforcement Learning Agent (Q-Learning)

State: masked pattern, wrong guess count, guessed letters

Action: choose a letter (a–z)

Reward: positive for correct guess, negative for wrong/repeat

Policy: epsilon-greedy with epsilon decay

Value Function: Q(s, a) updated using TD learning

Fallback mechanism:
When Q-values are not reliable (early stages), we blend:

Candidate frequency from dictionary filtering

HMM probabilities

to make informed guesses.Results
Metric	Value
Total test words	2000
Solved words	~401
Accuracy	~20%
Wrong guesses	~11113
Repeated guesses	0
Final Score	746,435

This score validates successful integration of HMM + RL for Hangman.

Contributors
Name	Contribution
Syed juneduddin S 	HMM  
Adarsha S R         RL implementation
M S Nandagopal      testing,debugging





