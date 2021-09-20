# Privacy guarantees of Fuzzy Message Detection
This repository is dedicated to analyse the privacy guarantees of [Fuzzy Message Detection](https://eprint.iacr.org/2021/089.pdf) (FMD). For a formal discussion on the topic, please refer to [our preprint](https://eprint.iacr.org/2021/1180.pdf) available on eprint.

This repository contains all the accompanying code and simulations we implemented and presented in our paper. You can see them all in this [Jupyter notebook](https://github.com/seresistvanandras/FMD-analysis/blob/main/src/Analyser.ipynb).

## FMD in a nutshell
Fuzzy Message Detection (FMD) is a recent cryptographic primitive invented by Beck et al. (CCS’21) where an untrusted server performs coarse message filtering for its clients in a recipient-anonymous way. In FMD — besides the true positive messages — the clients download from the server their cover messages determined by their false-positive detection rates. What is more, within FMD, the server cannot distinguish between genuine and cover traffic. Thus, the false-positive messages act as cover traffic for genuine messages.

FMD could have many potential applications. Hereby, we highlight two of them:
 * **Anonymous messaging**: In a recipient-anonymous messaging application, the senders post their recipient-anonymous messages to a store-and-forward server. If the server employs FMD, recipients can detect their incoming (and false-positive) messages in an efficient and privacy-enhanced way. Recently, the Niwl messaging application was deployed utilizing FMD.
 * **Privacy-preserving cryptocurrencies & stealth payments**: In privacypreserving cryptocurrencies, e.g., Monero, Zcash, or in a privacyenhancing overlay, payment recipients wish to detect their incoming payments without scanning the whole ledger. At the time of writing, several privacy-enhancing overlays for Ethereum (e.g., Zeth, Umbra) as well as for standalone cryptocurrencies (e.g., Penumbra) are actively exploring the possibility of applying FMD in their protocols.

## Information-Theoretical Privacy Guarantees
We assess and quantify the privacy and anonymity guarantees of FMD and the enhanced k-anonymity it provides in the context of anonymous communication systems. We focus on three notions of privacy and anonymity: recipient unlinkability, relationship anonymity, and temporal detection ambiguity. We demonstrate that FMD does not provide relationship anonymity when the server knows the senders’ identity. Concerning recipient unlinkability and temporal detection ambiguity, we show that they are only provided in a meaningful way when the system has extensive traffic and users apply considerable false-positive detection rates.

## Differential Privacy Analysis
We adopt differential privacy (DP) for the FMD scenario and coin a new definition, called Personalized Existing Edge Differential Privacy (PEEDP). Moreover, we analyze the number of incoming messages of a user with (ε, δ)-differential privacy. The uncovered trade-off between the FMD’s false-positive rates and DP’s parameters could help the users to determine the appropriate regimes of false-positive rates, which corresponds to the level of tolerated privacy leakage.

## Game-Theoretical Analysis
We formalize a game focusing on relationship anonymity and show that in our model at the Nash Equilibrium, the users do not employ any cover traffic via FMD due to their selfishness. On the other hand, if a central planner coordinates the false-positive rate selection (and a certain condition holds), then the highest welfare corresponds to the utilization of FMD.

## Simulation of FMD on Real-World Data
We quantitatively evaluate the privacy guarantees of FMD through open-source simulations on
real-world communication systems. Specifically, we show that the untrusted
server can effortlessly recover a large portion of the social graph of the communicating users, i.e., the server can break relationship anonymity for numerous users.
