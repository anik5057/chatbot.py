
import spacy

# spaCy NLP model load karna
nlp = spacy.load("en_core_web_sm")

# Responses dictionary
responses = {
    "hello": "Hi there! How can I help you today?",
    "hi": "Hello! What can I do for you?",
    "how are you": "I'm just a bot, but I'm functioning as expected!",
    "bye": "Goodbye! Have a great day.",
    "your name": "I'm ChatBot, your virtual assistant.",
    "help": "Sure! I'm here to help. Ask me anything."
}

# Function to get chatbot response
def get_response(user_input):
    doc = nlp(user_input.lower())

    for token in doc:
        if token.text in responses:
            return responses[token.text]

    return "I'm sorry, I didn't understand that. Can you rephrase?"

# Chatbot conversation loop
def chat():
    print("🤖 ChatBot: Hello! Type 'bye' to exit.")
    while True:
        user_input = input("You: ")
        if "bye" in user_input.lower():
            print("🤖 ChatBot: Goodbye! Take care.")
            break
        response = get_response(user_input)
        print("🤖 ChatBot:", response)

# Start chatbot
if __name__ == "__main__":
    chat()
