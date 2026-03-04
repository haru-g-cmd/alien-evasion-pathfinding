# Alien Evasion Pathfinding

A bot navigates a randomly generated 30x30 maze trying to reach a goal while an alien actively chases it. Four bot strategies are implemented, each one smarter than the last, and they're all benchmarked against each other across thousands of maze trials using multiprocessing. The alien moves one step toward the bot each turn using BFS with some randomness mixed in. The comparison shows how much each improvement in strategy actually matters in terms of survival rate.

Bot 1 plans a single BFS path at the start and follows it no matter what the alien does. Bot 2 replans with BFS every single step based on the alien's current position. Bot 3 also replans every step, but treats all cells within 2 steps of the alien as walls, giving it a safety buffer. Bot 4 goes further with a risk aware cost model where each cell's cost depends on its proximity to the alien, so the bot picks paths that balance progress toward the goal against how exposed it is.

The maze is regenerated for each trial, and a multiprocessing pool runs all four bots on the same set of mazes so the comparison is fair. Results are averaged over the full batch.
