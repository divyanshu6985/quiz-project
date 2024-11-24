# In-memory storage for users
users = {}

def register():
    username = input("Enter a username: ")
    if username in users:
        print("Username already exists! Please try a different one.")
        return False
    
    password = input("Enter a password: ")
    users[username] = password
    print("Registration successful!")
    return True

def login():
    username = input("Enter your username: ")
    password = input("Enter your password: ")
    
    if username in users and users[username] == password:
        print("Login successful!")
        return True
    
    print("Invalid username or password.")
    return False

def ask_question(question, options, correct_answer):
    print(question)
    for option in options:
        print(option)
    user_answer = input("Your answer (a/b/c): ").lower()
    return user_answer == correct_answer

def quiz():
    questions = [
        {
            "question": "How many colors are there in rainbow?",
            "options": ["(a) 7", "(b) 8", "(c) 6"],
            "answer": "a"
        },
        {
            "question": "Where is the Konark sun Temple located?",
            "options": ["(a) madhya pradesh", "(b) odisha", "(c) karnataka"],
            "answer": "b"
        },
        {
            "question": "where is TCS Headquarters in india?",
            "options": ["(a) Mumbai", "(b) Delhi", "(c) Pune"],
            "answer": "a"
        }
    ]

    score = 0
    for q in questions:
        if ask_question(q["question"], q["options"], q["answer"]):
            print("Correct!")
            score += 1
        else:
            print("Wrong! The correct answer is:", q["answer"])
        print()  # Newline for readability

    print("You scored", score, "out of", len(questions))

def main():
    while True:
        action = input("Do you want to (r)egister, (l)ogin, or (q)uit? ").lower()
        
        if action == 'r':
            register()
        elif action == 'l':
            if login():
                quiz()
        elif action == 'q':
            print("Goodbye!")
            break
        else:
            print("Invalid option, please try again.")

# Run the application
if _name_ == "_main_":
  main()
