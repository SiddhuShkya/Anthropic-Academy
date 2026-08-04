# Claude API Fundamentals Quiz

## Question 1
**You want to send a request to Claude's API. What's the minimum information you must include?**

- [ ] Only the API key and your question
- [ ] Just your message text
- [x] API key, model name, messages, and max tokens
- [ ] Your name, email, and message

## Question 2
**You ask Claude "What is pizza?" and it answers. Then you ask "What toppings are popular?" but Claude doesn't understand what you're referring to. What's the problem?**

- [ ] Your internet connection is slow
- [ ] Claude is broken
- [ ] You asked too quickly
- [x] Claude doesn't remember previous messages

## Question 3
**When Claude processes your text, what's the first thing it does?**

- [ ] Generates a response immediately
- [ ] Checks if it's appropriate content
- [x] Breaks it into smaller chunks called tokens
- [ ] Translates it to another language

## Question 4
**Users complain your chat app feels slow because they wait 20 seconds staring at a loading spinner, then all the generated text appears at once. What can fix this?**

- [ ] Asking shorter questions
- [ ] Using a faster internet connection
- [x] Enabling response streaming
- [ ] Using a different web browser

## Question 5
**You're building a web app that talks to Claude. Where should you store your API key?**

- [ ] In your mobile app that users install
- [ ] In a text file on the user's computer
- [x] On your server that users can't access
- [ ] In your JavaScript code that users download

## Question 6
**You're building a math tutor bot. You want Claude to give hints instead of direct answers. What should you use?**

- [ ] Setting a very low word limit
- [ ] Using all capital letters in your messages
- [x] A system prompt explaining the tutor role
- [ ] Asking users to be more specific

## Question 7
**You want Claude to give very predictable, consistent answers for a factual Q&A app. What temperature setting should you use?**

- [ ] Temperature doesn't matter for facts
- [x] Low temperature (near 0.0)
- [ ] Medium temperature (around 0.5)
- [ ] High temperature (near 1.0)

## Question 8
**You're building an app that needs clean JSON from Claude with no extra text or formatting. How do you get just the raw JSON?**

- [ ] Send the request multiple times and pick the best one
- [ ] Ask Claude very nicely to only return JSON
- [x] Combine prefilled messages and stop sequences
- [ ] Use a very high temperature setting