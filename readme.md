# Chicken Coop

* [Full paper](https://r.rachum.com/dh-paper)
* [Extended abstract](https://r.rachum.com/dh-ea-paper)
* [Slide deck](https://r.rachum.com/dh-deck)
* [Talk video](https://r.rachum.com/dh-video)

This is the accompanying code for our paper **Emergent Dominance Hierarchies in Reinforcement Learning Agents** to be presented at AAMAS 2024.

Abstract:

> Modern Reinforcement Learning (RL) algorithms are able to outperform humans in a wide variety of tasks. Multi-agent reinforcement learning (MARL) settings present additional challenges, and successful cooperation in mixed-motive groups of agents depends on a delicate balancing act between individual and group objectives. Social conventions and norms, often inspired by human institutions, are used as tools for striking this balance.
>
> In this paper, we examine a fundamental, well-studied social convention that underlies cooperation in both animal and human societies: Dominance hierarchies.
>
> We adapt the ethological theory of dominance hierarchies to artificial agents, borrowing the established terminology and definitions with as few amendments as possible. We demonstrate that populations of RL agents, operating without explicit programming or intrinsic rewards, can invent, learn, enforce, and transmit a dominance hierarchy to new populations. The dominance hierarchies that emerge have a similar structure to those studied in chickens, mice, fish, and other species.

Chicken Coop is a multi-agent environment in which agents learn to form dominance hierarchies with each other, like those that form in animal societies. The environment is a multi-player variant of the classic [game of chicken](https://en.wikipedia.org/wiki/Chicken_(game)).

![](https://i.imgur.com/XNMFhAr.png)

The figure above shows the aggressiveness levels of each of the six agents (depicted as differently-colored lines) in four sample Chicken Coop populations. The two populations in the top row form transitive dominance hierarchies, while the two populations in the bottom row form intransitive dominance hierarchies.

## Installation

Tested on Python 3.11.

```
# Set up virtualenv if needed:
python -m venv chicken-coop-env
source chicken-coop-env/bin/activate

pip install chicken-coop

# Run tests
_test_chicken_coop
```

## Usage


Basic run:

```
chicken_coop run
```

Main run used in the paper:

```
chicken_coop run --moniker paper-run --use-tune --n-tune-samples 300
```

Transplant experienced agents into a naive population:

```
chicken_coop transplant --moniker paper-transplant --visitor-trek \
  ~/.chicken_coop/<YOUR_PREVIOUS_RUN>
```

Ablate opponent perception accuracy:

```
chicken_coop run --moniker paper-ablate-observation --use-tune --n-tune-samples 10 \
  --observation-accuracy 0.0 \
  --observation-accuracy 0.1 \
  --observation-accuracy 0.2 \
  --observation-accuracy 0.3 \
  --observation-accuracy 0.4 \
  --observation-accuracy 0.5 \
  --observation-accuracy 0.6 \
  --observation-accuracy 0.7 \
  --observation-accuracy 0.8 \
  --observation-accuracy 0.9 \
  --observation-accuracy 1.0
```

Investigate non-linearity:

```
chicken_coop run --moniker paper-cycles --use-tune --n-tune-samples 30 --n-agents 12 \
  --learning-rate 3e-05
```

## Citing

If you used either the Chicken Coop module, or any insights from our paper, please cite our paper:

```
@inproceedings{rachum2024dh,
  title={Emergent Dominance Hierarchies in Reinforcement Learning Agents},
  author={Rachum, Ram and Nakar, Yonatan and Tomlinson, Bill and Alon, Nitay and Mirsky, Reuth},
  booktitle={International Workshop on Coordination, Organizations, Institutions, Norms, and Ethics for Governance of Multi-Agent Systems},
  pages={41--56},
  year={2024},
  organization={Springer}
}
```
