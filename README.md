# A* Search Algorithm for Robot Path Planning

This program uses A* `algorithm` to find an optimal path to get from point A to point B. Here, I utilized `data structures` (list, set, and dictionary) to provide optimal performance.

In this example, we have 40 nodes to represent intersections, each with their own unique sets of connections with other nodes to represent roads.

The image output is shown in my Jupyter notebook but are not included when I commit my project to GitHub. Thus, I have included 2 pictures:
- `show_map().png` to represent the 40 nodes on the map
- `show_map(test_path).png` to represent an optimal path from a start node to a goal node.

<img src="https://github.com/jacobsayono/a-star-algorithm/blob/main/screenshots/show_map().png" width="100%" height="100%" />

<img src="https://github.com/jacobsayono/a-star-algorithm/blob/main/screenshots/show_map(test_path).png" width="100%" height="100%" />

## Code Summary:

- If the heuristic is consistent, once a node is chosen by `get_current_node`, it is guaranteed that we found the best posible path from the start node to this node, and thus also the best possible g-score and f-score for this node. So, this "current" node is added to the closed set, and can be ignored if it appears again as a neighbor of another node in some iteration in the future.
- We explore the neighbors of `current` (some call this "expanding the node"). For each neighbor node:
    - If it is already in the closed set we ignore it.
    - We want to know if going from `start` to `neighbor` having `current` as its preceding or parent node in the path is better than the best path we have found so far for `neighbor`. If that is the case, we update the information for `neighbor`:
        - Its new g-score (not definitive, just the best found so far) is easy to calculate, since we know the definitve g-score of `current` and `neighbor` is adjacent to `current`.
        - Its new f-score is also easy, since the h-score is fixed.
        - We also update cameFrom updating or creating the key `neighbor` with the value `current`. This idea of keeping just the parent of each node and reconstructing the path backwards is better than keeping all the partial paths: it saves memory, and the reconstruction algorithm is linear, so fast enough in most scenarios.

See `a_star.ipynb` line comments for more details.

## To Run Locally:

- Install `JupyterLab` or `Jupyter Notebook` running on `Python3`
- Install `pip` for: `networkx`
- Install `nodejs` or `npm` for: `plotly`

See `map.py` header comments for more details.

## Common Q&A:

**1) How would we explain A-Star to a family member(layman)?**

- `A*` is a computer algorithm that takes us from point A to point B similar to how we humans, who usually don't like to take an unnecessary long route, get to places with the best directions!

**2) How does A-Star search algorithm differ from Uniform cost search? What about Best First search?**

- `Uniform Cost Search` is guaranteed to find the shortest path but spends a lot of time searching for possible nodes to explore. `Greedy Best-First Search` explores a small number of nodes in many cases but may take a longer path if there are obstacles in the way. `A-Star` combines the best of these two algorithms to find a very optimal path.

**3) What is a heuristic?**

- In the algorithm, a `heuristic` function returns the estimated overall "straight line" distance left toward the goal. Minimizing this value allows us to keep focused on getting closer to the goal despite obstacles.

**4) What is a consistent heuristic?**

- A `consistent heuristic` is a function where the cost of the estimated distance toward a neighboring node plus the cost of the estimated remaining distance toward the goal is always less than or equal to the total cost of the heuristic function.

**5) What is a admissible heuristic?**

- An `admissible heuristic` is a function that never overestimates the cost of reaching the goal.

**6) Admissible vs. consistent heuristics?**

- `Some` admissible heuristic are consistent, but `all` consistent heuristic are admissible.

## Future Explorations:

- How can I represent the path as a `linked list` of nodes with `pointers` in code?
- For frontier nodes, how can I implement a `priority queue` for removing best items and adding in new items?
- Building a set from a `hash table` or `tree`.
- What would be an example of a heuristic that is admissible but `not` consistent?
- Comparing algorithms between `Tree.Search()` vs. `Graph.Search()`.
