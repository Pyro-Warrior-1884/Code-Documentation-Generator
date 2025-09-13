# Code Documentation Generator (with Ollama AI)

This project automates the generation of developer-friendly technical documentation from any public GitHub repository. It clones a repository, scans its source code files, summarizes their purpose and structure using an Ollama AI model, and exports the results into a Word (.docx) file.

## Features

- **Clone any GitHub repository automatically**
- **Scans all relevant code files** (.py, .js, .jsx, .ts, .java, .cpp, .go, .rs, etc.)
- **Skips unnecessary directories** (node_modules, venv, **pycache**, etc.)
- **Splits large files into chunks** to handle long codebases
- **Uses Ollama's LLMs** (default: gemma:2b) for accurate file-level summaries
- **Generates a clean, structured Word document** with:
  - Repository metadata
  - Dependencies and configuration files
  - Per-file technical summaries
- **Runs efficiently** even on laptops with 8 GB RAM, thanks to lightweight Ollama models

## System Requirements

- **OS**: Windows, macOS, or Linux
- **RAM**: 8 GB or higher (lightweight Ollama models such as gemma:2b run comfortably on this setup)
- **Disk space**: At least 2 GB free (for cloned repositories and temporary files)
- **Internet connection** (for cloning repos and Ollama model downloads)

## Python Requirements

- **Python 3.8 or higher**
- Install dependencies with: `pip install -r requirements.txt`

**Requirements.txt** should contain:
```
GitPython
python-docx
requests
```

## Ollama Requirements

- Install Ollama from [https://ollama.ai](https://ollama.ai)
- Verify it is running locally (default: http://localhost:11434)
- Pull the default model with: `ollama pull gemma:2b`

## Usage

1. **Clone this tool:**
   ```bash
   git clone https://github.com/your-username/your-repo.git
   cd your-repo
   ```

2. **Run the script:**
   ```bash
   python docgen.py --repo <github_repo_url> --out documentation.docx
   ```

**Example:**
```bash
python docgen.py --repo https://github.com/psf/requests --out requests_docs.docx
```

### Command-line Options

- `--repo` or `-r` : **Required.** GitHub repo URL
- `--out` or `-o` : Output Word file name (default: documentation.docx)
- `--tmp` or `-t` : Temporary folder for cloned repo (default: ./Code_Repository)
- `--model` : Ollama model to use (default: gemma:2b)
- `--keep` : Keep cloned repo after summarization (default: deletes repo)

## Output

The generated Word (.docx) file will include:

- Repository details (URL, scan path)
- Dependency files (requirements.txt, package.json, etc.)
- Per-file breakdown with:
  - Purpose
  - Key components
  - Functionality
  - Dependencies
  - Edge cases

## Example Workflow

1. **You run:** `python docgen.py --repo https://github.com/some/project --out docs.docx`

2. **The script:**
   - Clones the repo to `./Code_Repository`
   - Scans files like .py, .js, .jsx, .ts
   - Summarizes code with Ollama (gemma:2b)
   - Produces `docs.docx`

3. **You get** a clean developer guide for the project in Microsoft Word.

## Notes

- The **gemma:2b** model is chosen for its balance of speed and accuracy. It runs smoothly even on laptops with 8 GB RAM, making this tool accessible without requiring a high-end GPU.
- For larger projects or deeper insights, you can switch to a bigger Ollama model by using:
  ```bash
  python docgen.py --repo <url> --model llama2:13b
  ```
- If no code files are found, the script will exit gracefully.

## License

This project is open-source. Use, modify, and adapt freely.

## Author

Developed by [Albert Augustine] (https://github.com/Pyro-Warrior-1884)
