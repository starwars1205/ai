
from collections import deque

grid = [
    ['S', '.', '.', '#', '.'],
    ['.', '#', '.', '#', '.'],
    ['.', '#', '.', '.', '.'],
    ['.', '#', '.', '#', '.'],
    ['.', '.', '.', '#', 'G']
]

ROWS, COLS = len(grid), len(grid[0])
start, goal = (0, 0), (4, 4)


class ModelBasedAgent:
    def __init__(self, start, goal):
        self.position = start
        self.start = start
        self.goal = goal
        self.internal_map = {}
        self.visited = set()
        self.path = []

    def perceive(self, grid):
        r, c = self.position
        for nr, nc in [(r,c), (r-1,c), (r+1,c),
                       (r,c-1), (r,c+1)]:
            if 0 <= nr < ROWS and 0 <= nc < COLS:
                self.internal_map[(nr,nc)] = grid[nr][nc]

    def is_valid(self, pos):
        r, c = pos
        return (0 <= r < ROWS and 0 <= c < COLS
                and self.internal_map.get(pos) != '#')

    def select_action(self, next_pos):
        r, c = self.position
        nr, nc = next_pos
        if nr < r: return "UP"
        if nr > r: return "DOWN"
        if nc < c: return "LEFT"
        if nc > c: return "RIGHT"

    def move(self, next_pos, grid):
        print("Action:", self.select_action(next_pos))
        self.position = next_pos
        self.perceive(grid)

    def find_path(self, grid):
        queue = deque([(self.start, [self.start])])
        self.visited = {self.start}

        while queue:
            pos, path = queue.popleft()
            self.position = pos
            self.perceive(grid)

            if pos == self.goal:
                return path

            r, c = pos
            for nr, nc in [(r-1,c), (r+1,c),
                           (r,c-1), (r,c+1)]:
                nxt = (nr, nc)
                if (self.is_valid(nxt) and nxt not in self.visited):
                    self.visited.add(nxt)
                    queue.append((nxt, path + [nxt]))

        return None

    def display_grid(self, grid):
        for r in range(ROWS):
            row = []
            for c in range(COLS):
                row.append('A' if (r,c) == self.position
                           else grid[r][c])
            print(' '.join(row))
        print()

    def run(self, grid):
        print("Initial Grid:")
        self.display_grid(grid)

        self.path = self.find_path(grid)

        if self.path is None:
            print("No path found!")
            return

        print("Path:", self.path)
        self.position = self.start

        for pos in self.path[1:]:
            self.move(pos, grid)
            self.display_grid(grid)

        print("Goal reached!")
        print("Total steps:", len(self.path) - 1)
        print("Visited cells:", len(self.visited))


agent = ModelBasedAgent(start, goal)
agent.run(grid)
