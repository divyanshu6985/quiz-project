# quiz-project
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
            "question": "What is the capital of France?",
            "options": ["(a) Paris", "(b) London", "(c) Berlin"],
            "answer": "a"
        },
        {
            "question": "What is 2 + 2?",
            "options": ["(a) 3", "(b) 4", "(c) 5"],
            "answer": "b"
        },
        {
            "question": "What is the color of the sky?",
            "options": ["(a) Blue", "(b) Green", "(c) Red"],
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
