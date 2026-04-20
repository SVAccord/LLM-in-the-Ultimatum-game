# LLM in the Ultimatum game

**Description**:
A study of the behavioral presets of large language models (LLM) with varying numbers of parameters was conducted using the professional characteristics of a participant in the two-player Ultimatum game as an example. The authors compared the behavior of LLMs in two roles: that of a direct player (Player A, proposing a division) and that of an advisor to a human player. The ISCO-08 classification of professions was used to define roles. Experiments were conducted on four modern LLMs (Phi-3.5-MoE-instruct, GPT-120b-oss, Qwen2.5-14b-Instruct, Qwen3-235B-A22B-Instruct). It was shown that there is a difference between the profession to which an LLM assigns its opponent by default and the profession from which it assumes the position of a holder when acting as a player. It was found that in the role of a player, LLMs tend to perceive themselves as a manager or expert, and the opponent as a representative of a less qualified profession. When transitioning to an advisory role, models typically recommend a lower share of the stake than they would otherwise, and their behavior becomes less differentiated across occupations. These results are important for understanding the hidden biases of LLMs and considering them when using them as autonomous agents and advisors in decision-making problems.

**Papper**: Сергеев В.А., Чхартишвили А.Г. Большая языковая модель (LLM) как игрок и как советник в игре «Ультиматум» // Управление большими системами. - 2026. - Вып. 120. - С.267-293.

We interact with the LLM via the API.
The LLM receives the game conditions and a description of their profession. Two situations are considered in terms of a division proposal: 
1. The LLM player must offer a share in the division to the second player (code provided).
2. The LLM advisor must offer advice to the human player regarding the second player's share in the division.
The proposal and acceptance of the proposal are modeled separately (basically the same code, but with a change in parsing the LLM's response)..

Two situations are also considered in terms of accepting the division: 
1. The LLM player must respond to the first player's proposed share in the division.
2. The LLM advisor must offer advice to the human player regarding the division proposed by the first player.
(The proposal and acceptance of the proposal are modeled separately.)

Some results in the offer situation:

**Таблица** Identification of the profession according to which LLM-player A plays. Distances L2 between vectors from Ari, i∈{1,…,10} and Arx, for LLM-player A. The lower the value, the better.

| Profession | Qwen2.5-14b-Instruct | Phi-3.5-MoE-instruct | Gpt120b-oss | Qwen3-235B-A22B-Instruct |
|------------|----------------------|----------------------|-------------|---------------------------|
| Manager | 0 | 0.47 | 0.95 | 0.18 |
| Expert | 0.1 | 0.65 | 0.57 | 0.13 |
| Technician | 0.1 | 0.48 | 0.84 | 0.3 |
| Clerk | 0.1 | 0.5 | 0.92 | 0.3 |
| Salesperson | 0.1 | 0.52 | 0.88 | 0.29 |
| Agricultural worker | 0.28 | 0.63 | 0.87 | 0.2 |
| Worker | 0.26 | 0.59 | 0.89 | 0.15 |
| Operator | 0.2 | 0.52 | 0.86 | 0.16 |
| Laborer | 0.2 | 0.56 | 0.95 | 0.18 |
| Military | 0.24 | 0.53 | 1.03 | 0.19 |


**Таблица** Identification of the profession in accordance with which the LLM-advisor recommends player A to act. Distances L2 between vectors from Ari, i∈{1,…,10} and the vector Arx, for the LLM-advisor of player A. The lower the value, the better.

| Profession | Qwen2.5-14b-Instruct | Phi-3.5-MoE-instruct | Gpt120b-oss | Qwen3-235B-A22B-Instruct |
|------------|----------------------|----------------------|-------------|---------------------------|
| Manager | 0.15 | 0.32 | 0.49 | 0.05 |
| Expert | 0.15 | 0.49 | 0.64 | 0.27 |
| Technician | 0.15 | 0.37 | 0.63 | 0.05 |
| Clerk | 0.11 | 0.49 | 0.69 | 0.10 |
| Salesperson | 0.15 | 0.41 | 0.57 | 0.11 |
| Agricultural worker | 0.15 | 0.28 | 0.56 | 0.05 |
| Worker | 0.15 | 0.31 | 0.60 | 0.11 |
| Operator | 0.15 | 0.32 | 0.44 | 0.05 |
| Laborer | 0.15 | 0.51 | 0.89 | 0.33 |
| Military | 0.21 | 0.32 | 0.71 | 0.07 |