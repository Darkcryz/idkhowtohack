import random

class MathQuiz:
    def __init__(self):
        self.score = 0
        self.difficulty = 1
        self.operations = ['+', '-', '*', '/']

    def get_problem(self):
        a = random.randint(1, self.difficulty*10)
        b = random.randint(1, self.difficulty*10)
        op = random.choice(self.operations)
        problem = f"{a} {op} {b}"
        answer = eval(problem)
        return problem, answer

    def play(self):
        print("Welcome to Math Quiz!")
        while True:
            problem, answer = self.get_problem()
            response = input(f"What is {problem}? ")
            if response == 'quit':
                break
            elif int(response) == answer:
                self.score += self.difficulty
                print(f"Correct! Your score is now {self.score}")
                if self.score % 10 == 0:
                    self.difficulty += 1
                    print(f"Difficulty increased to {self.difficulty}")
            else:
                self.score -= 1
                print(f"Incorrect! Your score is now {self.score}")

if __name__ == '__main__':
    game = MathQuiz()
    game.play()
