
# Simple Chatbot using Predefined Rules and Pattern Matching

def chatbot(user_input):
    user_input = user_input.lower()

    if "hello" in user_input or "hi" in user_input:
        return "Hello! How can I help you?"

    elif "how are you" in user_input:
        return "I am fine. Thank you!"

    elif "your name" in user_input:
        return "My name is SimpleBot."

    elif "college" in user_input:
        return "I can provide basic information about the college."

    elif "thank you" in user_input or "thanks" in user_input:
        return "You are welcome!"

    elif "bye" in user_input or "exit" in user_input:
        return "Goodbye! Have a nice day."

    else:
        return "Sorry, I don't understand your question."


print("Simple Chatbot")
print("Type 'bye' or 'exit' to stop.")

while True:
    user_input = input("You: ")
    response = chatbot(user_input)
    print("Bot:", response)

    if "bye" in user_input.lower() or "exit" in user_input.lower():
        break
