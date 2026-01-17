# 📋 Dir2Clip

**Dir2Clip** is a Python CLI tool designed to streamline the process of sharing code context with Large Language Models (LLMs) like ChatGPT, Claude, and Gemini. 

It recursively scans a directory, intelligently filters files, formats their contents into a single structured string, and copies the result directly to your clipboard—ready to paste.

## ✨ Features

- **🚀 Instant Clipboard Copy**: No manual selecting or copying. One command and you're ready to paste.
- **🌲 Recursive Scanning**: Traverses your project structure to capture all relevant files.
- **🚫 Smart Filtering**:
  - Automatically ignores binary files (images, compiled code, etc.).
  - Skips standard noise like `.git`, `venv`, `node_modules`, `__pycache__`.
- **📏 Context Limit Protection**: 
  - Prevents clipboard overflow for browser-based LLMs.
  - Defaults to 100,000 characters (configurable).
  - Adds a clear warning footer if content is truncated.
- **📝 LLM-Friendly Formatting**: 
  - Wraps file contents in Markdown code blocks.
  - Clearly labels each file with `### FILE: path/to/file.ext` for optimal model understanding.

## 🛠️ Installation

You can install **Dir2Clip** directly from PyPI:

```bash
pip install dir2clip
```

**Linux Users:** You may need a system clipboard utility if one isn't already installed:
```bash
sudo apt-get install xclip  # or xsel
```

### Installing from Source (For Developers)

1. **Clone the repository**:
   ```bash
   git clone https://github.com/yourusername/Dir2Clip.git
   cd Dir2Clip
   ```

2. **Install the package in editable mode**:
   ```bash
   pip install -e .
   ```

## 📖 Usage

Once installed, you can run `dir2clip` from anywhere in your terminal:

```bash
# Scan and copy current directory
dir2clip

# Scan and copy a specific directory
dir2clip /path/to/project

# Set a custom character limit
dir2clip --max-len 50000

# View all options
dir2clip --help
```

### Output Example

When you paste into your LLM, it will look like this:

```text
### FILE: src/main.py
```
import os
print("Hello World")
```

### FILE: README.md
```
# My Project
...
```
```

## ⚙️ Configuration

You can customize the `IGNORE_DIRS` list inside `dir2clip/core.py` to exclude additional folders:

```python
IGNORE_DIRS = {'.git', 'venv', 'node_modules', 'dist', 'build', ...}
```

## 📄 License

MIT
