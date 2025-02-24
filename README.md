#HANG-MAN GAME (python code)

    import random

    words = ['apple','orange','tree','ball','void']
    hangman_art = {
        0 : ("   ",
             "   ",
             "   "),
        1 : (" o ",
             "   ",
             "   "),
        2 : (" o ",
             " | ",
             "   "),
        3 : (" o ",
             "/| ",
             "   "),
        4 : (" o ",
             "/|\\",
             "   "),
        5 : (" o ",
             "/|\\",
             "/  "),
        6 : (" o ",
             "/|\\",
             "/ \\")
    } 

    def display_man(wrong_guesses):
        for line in hangman_art[wrong_guesses]:
            print(line)
            
    def display_hint(hint):
        print(" ".join(hint))

    def display_answer(answer):
        print(" ".join(answer))
 
    def main():
        ans = random.choice(words)
        hint = ['_'] * len(ans)
        wrong_guesses = 0
        guessed_letters = set()
        is_running = True
    
        while is_running:     
            display_man(wrong_guesses)
            display_hint(hint)
            guess = input("Guess the letter: ").lower()

            if  len(guess) !=1 and guess.isalpha :
                print("INVALID INPUT")
                continue

            if (guess in guessed_letters):
                print(f"{guess} is already guessed")
                continue

            guessed_letters.add(guess)

            if guess in ans :
                for i in range(len(ans)):
                    if ans[i] == guess:
                        hint[i] = guess
            else: 
                wrong_guesses += 1

            if "_" not in hint:
                display_man(wrong_guesses)
                display_answer(ans)
                print("YOU WIN!")
                is_running = False   
            elif wrong_guesses >= len(hangman_art) - 1:
                display_man(wrong_guesses)
                display_answer(ans)
                print("YOU LOSE!")  
                is_running = False  

    if __name__ == '__main__':
        main()
