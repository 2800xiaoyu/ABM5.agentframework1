# ABM5.agentframework1
import random

class Agent():
    pass

class Agent:
    def __init__(self, i, environment, n_rows, n_cols):
        """
        The constructor method.

        Parameters
        ----------
        i : Integer
            To be unique to each instance.
        environment : List
            A reference to a shared environment
        n_rows : Integer
            The number of rows in environment.
        n_cols : Integer
            The number of columns in environment.
        Returns
        -------
        None.
        """
        self.i = i
        self.environment = environment
        tnc = int(n_cols / 3)
        self.x = random.randint(tnc - 1, (2 * tnc) - 1)
        tnr = int(n_rows / 3)
        self.y = random.randint(tnc - 1, (2 * tnr) - 1)
        self.store = 0
        pass
    
    def __str__(self):
        return self.__class__.__name__ + "(x=" + str(self.x) \
            + ", y=" + str(self.y) + ", i=" + str(self.i) + ")"
    
    def __repr__(self):
        return str(self)
    
    def move(self, x_min, y_min, x_max, y_max):
        rn = random.randint(0, 99)
        if rn < 55:
            self.x = self.x + 2
        else:
            self.x = self.x - 2
        # Change y-coordinate
        rn = random.randint(0, 99)
        if rn > 55:
            self.y = self.y - 2
        else:
            self.y = self.y + 2
        # Apply movement constraints
        if self.x < x_min:
            self.x = x_min
        if self.y < y_min:
            self.y = y_min
        if self.x > x_max:
            self.x = x_max
        if self.y > y_max:
            self.y = y_max
    
    def eat(self):
        if self.environment[self.y][self.x] >= 10:
            self.environment[self.y][self.x] -= 10
            self.store += 10
