### The Ripple-Spreading Algorithm for the Shortest Path Tour Problem

##### Reference: Ma Y M, Zhou H, Hu X B. An efficient nature-inspired method to solve the shortest path tour problem[C]//2021 IEEE Symposium Series on Computational Intelligence (SSCI). IEEE, 2021: 1-6.

The shortest path tour problem aims to find the shortest path that traverses multiple disjoint node subsets in a given order.

----

| Variables     | Meaning                                                      |
| ------------- | ------------------------------------------------------------ |
| network       | Dictionary, {node1: {node2: length, node3: length, ...}, ...} |
| node_subset   | List, [[subset1], [subset2], ...]                            |
| source        | List, the source nodes of this subproblem of SPTP            |
| destination   | List, the destination nodes of this subproblem of SPTP       |
| init_time     | List, the initial time that should generate initial ripples at source nodes |
| init_radius   | List, the initial radius of initial ripples at source nodes  |
| nn            | The number of nodes                                          |
| neighbor      | Dictionary, {node1: [the neighbor nodes of node1], ...}      |
| v             | The ripple-spreading speed (i.e., the minimum length of arcs) |
| t             | The simulated time index                                     |
| nr            | The number of ripples - 1                                    |
| epicenter_set | List, the epicenter node of the ith ripple is epicenter_set[i] |
| path_set      | List, the path of the ith ripple from the source node to node i is path_set[i] |
| radius_set    | List, the radius of the ith ripple is radius_set[i]          |
| active_set    | List, active_set contains all active ripples                 |
| Omega         | Dictionary, Omega[n] = i denotes that ripple i is generated at node n |

----

#### Example

![](https://github.com/Xavier-MaYiMing/The-ripple-spreading-algorithm-for-the-shortest-path-tour-problem/blob/main/SPTP_example.png)

The SPTP example has four disjoint node subsets: $\{0\}, \{1, 3\}, \{4, 5\}, \{6\}$. The aim is to find the shortest path from node 0 to node 6 that traverse at least one node in $\{1, 3\}$ and $\{4, 5\}$. The optimal solution of the SPTP is $0\rightarrow3\rightarrow4\rightarrow6$.

```python
if __name__ == '__main__':
    test_network = {
        0: {1: 2, 2: 3, 3: 3},
        1: {0: 2, 3: 2},
        2: {0: 3, 3: 3},
        3: {0: 3, 1: 2, 2: 3, 4: 2, 5: 3, 6: 3},
        4: {3: 2, 6: 2},
        5: {3: 3, 6: 3},
        6: {3: 3, 4: 2, 5: 3},
    }
    subset = [[0], [1, 3], [4, 5], [6]]
    print(main(test_network, subset))
```

##### Output

```python
{'path': [0, 3, 4, 6], 'length': 7}
```

