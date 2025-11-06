# Reflection Log - Assignment 2: Multi-Agent Travel Planner

## What I Learned from Multi-Agent Workflow

Working on this multi-agent travel planner taught me how splitting tasks between specialized agents can produce better results than using a single agent. The Planner Agent focuses purely on creating comprehensive itineraries from its knowledge base, while the Reviewer Agent handles the validation and fact-checking with real-time internet searches. This separation of concerns is similar to how teams work in real life - one person generates ideas, another verifies them.

I learned that prompt engineering is really important for agent behavior. The way I structured the instructions directly affected how detailed and useful the outputs were. For example, explicitly telling the Reviewer to create a "Delta List" made the validation process transparent and easy to understand. Without clear format requirements, the agents would produce inconsistent results.

The multi-agent approach also showed me how agents can complement each other's weaknesses. The Planner can be creative without worrying about perfect accuracy, and the Reviewer catches mistakes. This is more efficient than trying to make one agent do both jobs at once.

## Challenges and Solutions

The biggest challenge was getting the environment setup working correctly. Initially, the API keys weren't loading from the .env file, causing authentication errors. I solved this by using export commands to set environment variables directly in the terminal session before running the app.

Another challenge was making the Reviewer actually use the internet_search tool effectively. My first version of the instructions was too vague, and the Reviewer would sometimes skip searches or ask for more information instead of validating. I fixed this by being very specific about what to search for and including example search queries like "[Museum name] opening hours 2025" in the instructions.

Getting the right balance in the Planner's output was tricky too. If it was too detailed, it would make up specific information. If too vague, the Reviewer couldn't validate properly. I found that having the Planner provide specific venue names and rough estimates worked best, letting the Reviewer refine the details.

## Creative Design Choices

I designed the workflow to mirror how humans plan trips. The Planner is optimistic and creative, focusing on matching activities to user interests without being overly concerned about perfect details. The Reviewer plays the critical role, questioning everything and using real data to improve the plan.

For the prompt design, I kept the language conversational and straightforward rather than overly formal or technical. This seemed to help the agents produce more natural-sounding outputs. I also made sure the Reviewer doesn't just delete things it can't verify - instead it marks them as "unverified" so the itinerary stays useful even when searches don't return perfect information.

The Delta List format was a deliberate choice to make the validation process transparent. Users can see exactly what was changed and why, which builds trust in the system and helps them understand which parts of the itinerary are verified versus estimated.

## External Tools and AI Assistance Used

- **Claude AI (Anthropic)**: Used for understanding the assignment requirements, debugging environment setup issues, and improving prompt engineering. The AI assistant helped me understand how to structure agent instructions and provided examples of effective prompts.

- **Tavily API**: Provides the internet search functionality for the Reviewer Agent to validate itinerary details.

- **OpenAI GPT-4o**: The underlying model for both Planner and Reviewer agents.

- **Streamlit**: Framework for building the web interface.

- **GitHub Copilot**: Occasionally used for code completion and syntax suggestions.

The AI assistance was particularly helpful for debugging the environment variable loading issues and understanding how to properly structure the agent instructions for optimal performance.