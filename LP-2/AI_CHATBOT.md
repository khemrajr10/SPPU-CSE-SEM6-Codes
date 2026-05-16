Practical5_AIchatbot

 Develop an elementary chatbot for any suitable customer interaction application.

Code:

# ---------------------------------------------------
# Elementary Chatbot for Customer Interaction
# ---------------------------------------------------

print("===================================")
print(" Welcome to Customer Support Bot ")
print("===================================")

# Infinite loop for continuous chatting
while True:

    # Take user input
    user = input("\nYou: ").lower()

    # Improved Greeting Handling
    if user in ["hello", "hi", "hey", "good morning", "good afternoon", "good evening"]:

        print("Bot: Hello! Welcome to Customer Support.")
        print("Bot: How can I help you today?")

    # Asking chatbot status
    elif "how are you" in user:

        print("Bot: I am fine and ready to help you!")

    # Asking about products
    elif "product" in user:

        print("Bot: We provide laptops, mobiles and accessories.")

    # Asking about price
    elif "price" in user:

        print("Bot: Prices depend on the product model.")

    # Asking about delivery
    elif "delivery" in user:

        print("Bot: Delivery usually takes 3 to 5 days.")

    # Asking about payment
    elif "payment" in user:

        print("Bot: We support UPI, Debit Card and Credit Card.")

    # Asking about return policy
    elif "return" in user:

        print("Bot: Products can be returned within 7 days.")

    # Asking contact details
    elif "contact" in user:

        print("Bot: You can contact us at support@email.com")

    # Exit condition
    elif user in ["bye", "exit", "quit"]:

        print("Bot: Thank you for visiting. Have a nice day!")
        break

    # Unknown input
    else:

        print("Bot: Sorry, I did not understand your question.")

