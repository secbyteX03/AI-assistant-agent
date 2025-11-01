# 🤖 AI Assistant Agent


## 🚀 Project Overview

AI Assistant Agent is a powerful, customizable AI assistant built using Google's Agent Development Kit (ADK). This project provides a foundation for creating intelligent agents that can understand natural language, answer questions, and assist with various tasks using the power of large language models.

### ✨ Key Features
- **Natural Language Understanding**: Built on advanced LLM technology for human-like conversations
- **Customizable Behavior**: Easily modify the agent's instructions and personality
- **Web Interface**: Built-in web interface for easy interaction
- **Extensible**: Add custom tools and functionality as needed
- **Powered by Gemini**: Utilizes Google's Gemini model for high-quality responses


## 📋 Getting Started

### Clone the Repository

To get started with this AI Assistant Agent, clone the repository using the following command:

```bash
git clone https://github.com/secbyteX03/AI-assistant-agent.git
cd AI-assistant-agent
```

## What is an ADK Agent?

The `LlmAgent` (often aliased simply as `Agent`) is a core component in ADK that acts as the "thinking" part of your application. It leverages the power of a Large Language Model (LLM) for:
- Reasoning
- Understanding natural language
- Making decisions
- Generating responses
- Interacting with tools

Unlike deterministic workflow agents that follow predefined paths, an `LlmAgent`'s behavior is non-deterministic. It uses the LLM to interpret instructions and context, deciding dynamically how to proceed, which tools to use (if any), or whether to transfer control to another agent.

## Required Agent Structure

For ADK to discover and run your agents properly (especially with `adk web`), your project must follow a specific structure:

```
parent_folder/
    agent_folder/         # This is your agent's package directory
        __init__.py       # Must import agent.py
        agent.py          # Must define root_agent
        .env              # Environment variables
```

### Essential Components:

1. **`__init__.py`**
   - Must import the agent module: `from . import agent`
   - This makes your agent discoverable by ADK

2. **`agent.py`**
   - Must define a variable named `root_agent`
   - This is the entry point that ADK uses to find your agent

3. **Command Location**
   - Always run `adk` commands from the parent directory, not from inside the agent directory
   - Example: Run `adk web` from the parent folder that contains your agent folder

This structure ensures that ADK can automatically discover and load your agent when running commands like `adk web` or `adk run`.

## Key Components

### 1. Identity (`name` and `description`)
- **name** (Required): A unique string identifier for your agent
- **description** (Optional, but recommended): A concise summary of the agent's capabilities. Used for other agents to determine if they should route a task to this agent.

### 2. Model (`model`)
- Specifies which LLM powers the agent (e.g., "gemini-2.0-flash")
- Affects the agent's capabilities, cost, and performance

### 3. Instructions (`instruction`)
The most critical parameter for shaping your agent's behavior. It defines:
- Core task or goal
- Personality or persona
- Behavioral constraints
- How to use available tools
- Desired output format

### 4. Tools (`tools`)
Optional capabilities beyond the LLM's built-in knowledge, allowing the agent to:
- Interact with external systems
- Perform calculations
- Fetch real-time data
- Execute specific actions

## 🛠️ Setup and Installation

### Prerequisites

- Python 3.8 or higher
- Git
- Google Cloud account with billing enabled
- Google AI API key

### Setup Environment

You only need to create one virtual environment for all examples in this course. Follow these steps to set it up:

```bash
# Create virtual environment in the root directory
python -m venv .venv

# Activate (each new terminal)
# macOS/Linux:
source .venv/bin/activate
# Windows CMD:
.venv\Scripts\activate.bat
# Windows PowerShell:
.venv\Scripts\Activate.ps1

# Install dependencies
pip install -r requirements.txt
```

Once set up, this single environment will work for all examples in the repository.

### Setting Up API Keys

1. Create an account in Google Cloud https://cloud.google.com/?hl=en
2. Create a new project
3. Go to https://aistudio.google.com/apikey
4. Create an API key
5. Assign key to the project
6. Connect to a billing account

The project includes a `.env.example` file in the `helpful_AI_agent` directory. To set it up:

1. Navigate to the agent directory:
   ```bash
   cd helpful_AI_agent
   ```
2. Rename `.env.example` to `.env`:
   ```bash
   ren .env.example .env
   ```
3. Open the `.env` file and replace the placeholder with your API key:
   ```
   GOOGLE_API_KEY=your_api_key_here
   GOOGLE_GENAI_USE_VERTEXAI=FALSE
   ```
4. Return to the project root directory:
   ```bash
   cd ..
   ```

## Running the Agent

To run this agent, you'll use the ADK CLI tool which provides several ways to interact with your agent:

1. Navigate to the project root directory (helpful_AI) containing your agent folder (helpful_AI_agent).
2. Start the interactive web UI:
```bash
adk web
```

3. Access the web UI by opening the URL shown in your terminal (typically http://localhost:8000)

4. Select your agent from the dropdown menu in the top-left corner of the UI( we only have one agent so you will only see one, but you can always add as many agents as you want)

5. Start chatting with your agent in the textbox at the bottom of the screen

### Troubleshooting

If your agent doesn't appear in the dropdown menu:
- Make sure you're running `adk web` from the parent directory (helpful_AI), not from inside the agent directory (helpful_AI_agent)
- Check that your `__init__.py` properly imports the agent module
- Verify that `agent.py` defines a variable named `root_agent`

### Alternative Run Methods

The ADK CLI tool provides several options:

- **`adk web`**: Launches an interactive web UI for testing your agent with a chat interface
- **`adk run [agent_name]`**: Runs your agent directly in the terminal
- **`adk api_server`**: Starts a FastAPI server to test API requests to your agent
you can see all these options by typing `adk --help` in the terminal

### Example Prompts to Try

- "How do you say hello in Spanish?"
- "What's a formal greeting in Japanese?"
- "Tell me how to greet someone in French"

You can exit the conversation or stop the server by pressing `Ctrl+C` in your terminal.

## 🐛 Reporting Issues

Found a bug or have a feature request? Please help us improve by:

1. Searching the [existing issues](https://github.com/secbyteX03/AI-assistant-agent/issues) to avoid duplicates
2. Creating a new issue with a clear title and description
3. Including steps to reproduce the issue (if applicable)
4. Adding any relevant error messages or screenshots

## 🤝 Contributing

We welcome contributions from the community! Here's how you can help:

1. **Fork** the repository
2. Create a **branch** for your feature (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add some amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. Open a **Pull Request**

Please ensure your code follows the project's coding standards and includes appropriate tests.

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Built with [Google's Agent Development Kit (ADK)](https://developers.google.com/agent-development-kit)
- Powered by [Google's Gemini](https://ai.google/discover/gemini/) AI model
- Thanks to all contributors who help improve this project!
