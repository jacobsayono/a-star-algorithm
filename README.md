# A* Search Algorithm for Robot Path Planning

This program uses A* to find an optimal path to get from point A to point B.

In this example, we have 40 nodes to represent intersections, each with their own unique sets of connections with other nodes to represent roads.

The image output is shown in my Jupyter notebook but are not included when I commit my project to GitHub.

Thus, I have included 2 pictures to 1) represent the 40 nodes on the map and 2) represent an optimal path from a start node to a goal node.

## Q&A:

 - How would I explain A-Star to a family member(layman)?

A* is a computer algorithm that takes us from point A to point B similar to how we humans, who usually don't like to take an unnecessary long route, get to places with the best directions!

- How does A-Star search algorithm differ from Uniform cost search? What about Best First search?

Uniform Cost Search is guaranteed to find the shortest path but spends a lot of time searching for possible nodes to explore. Greedy Best-First Search explores a small number of nodes in many cases but may take a longer path if there are obstacles in the way. A-Star combines the best of these two algorithms to find a very optimal path.

- What is a heuristic?

In our algorithm, a heuristic function returns the estimated overall "straight line" distance left toward the goal. Minimizing this value allows us to keep focused on getting closer to the goal despite obstacles.

- What is a consistent heuristic?

A consistent heuristic is a function where the cost of the estimated distance toward a neighboring node plus the cost of the estimated remaining distance toward the goal is always less than or equal to the total cost of the heuristic function.

- What is a admissible heuristic?

An admissible heuristic is a function that never overestimates the cost of reaching the goal.

- Some admissible heuristic are consistent, but all consistent heuristic are admissible.
