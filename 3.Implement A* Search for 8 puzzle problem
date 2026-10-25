import heapq

start = (1, 2, 3,
         4, 0, 6,
         7, 5, 8)

goal = (1, 2, 3,
        4, 5, 6,
        7, 8, 0)


def heuristic(state):
    distance = 0

    for i, tile in enumerate(state):
        if tile != 0:
            j = goal.index(tile)
            distance += abs(i // 3 - j // 3)
            distance += abs(i % 3 - j % 3)

    return distance


def get_neighbors(state):
    neighbors = []
    zero = state.index(0)
    row, col = zero // 3, zero % 3

    for dr, dc in [(0, 1), (0, -1), (1, 0), (-1, 0)]:
        r, c = row + dr, col + dc

        if 0 <= r < 3 and 0 <= c < 3:
            pos = r * 3 + c
            new_state = list(state)
            new_state[zero], new_state[pos] = new_state[pos], new_state[zero]
            neighbors.append(tuple(new_state))

    return neighbors


def astar():
    queue = [(heuristic(start), 0, start)]
    cost = {start: 0}
    parent = {start: None}

    while queue:
        f, g, state = heapq.heappop(queue)

        if g != cost[state]:
            continue

        if state == goal:
            path = []

            while state is not None:
                path.append(state)
                state = parent[state]

            return path[::-1]

        for next_state in get_neighbors(state):
            new_cost = g + 1

            if new_cost < cost.get(next_state, float('inf')):
                cost[next_state] = new_cost
                parent[next_state] = state
                f = new_cost + heuristic(next_state)
                heapq.heappush(queue, (f, new_cost, next_state))

    return None


path = astar()

if path:
    print("Initial State:")
    for i in range(0, 9, 3):
        print(start[i:i+3])

    print("\nSolution Path:")

    for step, state in enumerate(path):
        print("Step", step)

        for i in range(0, 9, 3):
            print(state[i:i+3])

        print()

    print("Goal reached!")
    print("Total moves:", len(path) - 1)

else:
    print("No solution found!")
