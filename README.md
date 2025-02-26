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


Alarm clock (python code)

    import time
    import datetime
    import pygame
    
    def set_alarm(alarm_time):
        print(f"Alarm set for {alarm_time} ")
        is_running = True
        sound_file = "Sweaty Linen - Surf Ninja 3.mp3"

        while is_running:
            current_time = datetime.datetime.now().strftime("%H:%M:%S")
            print(current_time)

            if current_time == alarm_time:
                print("WAKE UP 😴😴🥱")

                pygame.mixer.init
                pygame.mixer.music.load(sound_file)
                pygame.mixer.music.play

                while pygame.mixer.music.get_busy:
                    time.sleep(1)
                is_running =False

            time.sleep(1)

    if __name__ == '__main__':
        alarm_time = input("Set the alarm time (HH:MM:SS): ")
        set_alarm(alarm_time)

        
