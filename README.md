# Agent Gatto 🐱

_Agent Gatto is at your service!_ 🎩

![Agent Gatto](https://avatars.githubusercontent.com/u/58954450?s=400&u=314d41ef1c2ecac0a73fd5c1b4c6069f75ce88ee&v=4)

This is not like other AI wrappers - this is the gatto's own wizardry wrapper! An AI-powered coding assistant that uses Google's Gemini 2.0 Flash model to help with code analysis, file manipulation, and Python execution within a controlled working directory. Agent Gatto combines the power of advanced AI with the cunning of a cat to solve your coding problems with style.

## Features

- **File Operations**: List, read, and write files within a secure working directory
- **Python Execution**: Run Python scripts with optional arguments and capture output
- **AI-Powered Analysis**: Leverage Google's Gemini 2.0 Flash model for intelligent code assistance
- **Function Calling**: Advanced function calling capabilities for complex tasks
- **Verbose Mode**: Debug mode for detailed operation logging
- **Security**: All operations are constrained to a specified working directory

## Installation

1. Clone the repository:

```bash
git clone https://github.com/davutkulaksiz/agent-gatto.git
cd agent-gatto
```

2. Install dependencies using uv (recommended):

```bash
uv sync
```

Or using pip:

```bash
pip install -r requirements.txt
```

3. Set up your environment variables:
   Create a `.env` file in the root directory and add your Gemini API key:

```bash
GEMINI_API_KEY=your_actual_gemini_api_key_here
```

## Usage

### Basic Usage

```bash
uv run main.py "your prompt here"
```

### With Verbose Mode (shows token usage metadata)

```bash
uv run main.py "your prompt here" --verbose
```

The `--verbose` flag is optional but will show useful metadata like how many tokens were used in the conversation.

### Examples

```bash
# Analyze and fix code issues
uv run main.py "How do I fix the calculator?"

# Get help with implementation
uv run main.py "Add error handling to the main function" --verbose

# Code review and suggestions
uv run main.py "Review the calculator code and suggest improvements"
```

## Available Functions

The AI assistant has access to the following functions:

### `get_files_info`

Lists files in the specified directory with their sizes and types.

### `get_file_content`

Reads and returns the content of a specified file.

### `run_python_file`

Executes a Python file with optional arguments and returns the output.

### `write_file`

Creates or overwrites a file with the specified content.

## Configuration

The project uses several configuration parameters defined in `config.py`:

- `MAX_CHARS`: Maximum characters for file operations (default: 10000)
- `WORKING_DIR`: The working directory for all operations (default: "./calculator")
- `MAX_ITERS`: Maximum iterations for the conversation loop (default: 20)

## Project Structure

```
agent-gatto/
├── main.py                 # Entry point and main application logic
├── config.py               # Configuration settings
├── prompts.py              # System prompt for the AI agent
├── call_function.py        # Function calling orchestration
├── functions/              # Available function implementations
│   ├── get_files_info.py   # File listing functionality
│   ├── get_file_content.py # File reading functionality
│   ├── run_python.py       # Python execution functionality
│   └── write_file.py       # File writing functionality
├── calculator/             # Example project (working directory)
│   ├── main.py
│   ├── pkg/
│   │   ├── calculator.py
│   │   └── render.py
│   ├── README.md
│   └── tests.py
├── requirements.txt        # Python dependencies
├── pyproject.toml          # Project metadata
└── README.md               # This file
```

## Requirements

- Python 3.9+
- Google Gemini API key
- Dependencies listed in `requirements.txt`

## Dependencies

- `google-genai==1.12.1`: Google Gemini API client
- `python-dotenv==1.1.0`: Environment variable management

## Security Features

- All file operations are constrained to the working directory
- Path traversal protection prevents access to files outside the working directory
- Subprocess execution is limited to Python files within the working directory
- 30-second timeout for Python script execution

## Development

### Running Tests

```bash
python tests.py
```

### Example Project

The repository includes a calculator project in the `calculator/` directory that serves as an example of how the agent can interact with and modify code within a project.
