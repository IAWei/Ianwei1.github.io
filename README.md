import random

planets = ["Mercury","Venus","Earth","Mars","Jupiter", "Saturn","Uranus","Neptune"]
continents = ["North America","South America","Australia","Europe","Asia","Africa","Antartica"]
mistakes = 0
max_mistakes = 6
guessed_letters = []

#MISTAKE DRAWER
def draw_hangman(mis):
  print("You made",mis,"mistake(s)")
  #NO MISTAKES
  if mis == 0:
    print("-----")
    print("|   |")
    print("|")
    print("|")
    print("|")
    print("|")
    print("-----")
  # 1 MISTAKES
  if mis == 1:
    print("-----")
    print("|   |")
    print("|   O")
    print("|")
    print("|")
    print("|")
    print("-----")
  # 2 MISTAKES
  if mis == 2:
    print("-----")
    print("|   |")
    print("|   O")
    print("|   |")
    print("|")
    print("|")
    print("-----")
  # 3 MISTAKES
  if mis == 3:
    print("-----")
    print("|   |")
    print("|   O")
    print("|  -|")
    print("|")
    print("|")
    print("-----")
  # 4 MISTAKES
  if mis == 4:
    print("-----")
    print("|   |")
    print("|   O")
    print("|  -|-")
    print("|")
    print("|")
    print("-----")
  # 5 MISTAKES
  if mis == 5:
    print("-----")
    print("|   |")
    print("|   O")
    print("|  -|-")
    print("|  /")
    print("|")
    print("-----")
  # 5 MISTAKES
  if mis == 5:
    print("-----")
    print("|   |")
    print("|   O")
    print("|  -|-")
    print("|  /")
    print("|")
    print("-----")  
  # 6 MISTAKES
  if mis == 6:
    print("-----")
    print("|   |")
    print("|   O")
    print("|  -|-")
    print("|  / /")
    print("|")
    print("-----") 

    
draw_hangman(5)    
    
    
    
    
#SELECTED WORD ASKING
#CATEGORY REAL OR FAKE
#SELECTED_WORD VARIABLE ASSIGNING
def pick_word():
  global selected_word
  while True:
    choice = input("Would you like Planets or continents?:")
  #VALID CHOICE (-PLANETS -CONTINENTS-)
    #PLANETS CHOICE
    if choice.lower() == "planets":
      selected_word = random.choice(planets).lower()
      print("Planets. WOW! Looks like we're going Extraterrestrial")
      return
    #CONTINENTS CHOICE
    if choice.lower() == "continents":
      selected_word = random.choice(continents).lower()
      print("Countries, huh? Guess it's time for a GEOGRAPHY TEST!! ")
      return
    else:
      print("\nPlease choose a valid category.\n")

#GUESS LETTER ALLOW
#MISTAKE ADDED IF INCORRECT
#LETTER ADDED ON GUESS LIST
def guess():
  my_guess = input("Guess a letter?:")
  if my_guess not in selected_word:
    global mistakes
    mistakes = mistakes + 1
  # Fixed tabbing
  guessed_letters.append(my_guess)

def make_blanks():
  output = ""
  for letter in selected_word:
    if letter in guessed_letters or letter == " ":
      output += letter
    else:
      output += "-"
  print(guessed_letters)
  if "-" not in output:
    print("YOU WIN!!!!\n\n\n")
    print("Created by Ian Wei and revised by Mark")
  return(output)

#FINAL FUNCTION

# filled out missing code from "run()"
def run():
  print("Welcome to hangman!!!")
  pick_word()
  while mistakes <= max_mistakes and "-" in make_blanks():
    draw_hangman(mistakes)
    print(make_blanks())
    guess()

run()
