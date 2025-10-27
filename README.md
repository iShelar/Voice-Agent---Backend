# Voice-Agent---Backend

## Setting Up a Python Virtual Environment

To create and activate a Python virtual environment for the project, follow these steps:

1. **Ensure Python 3 is installed**  
   Check your Python version:
   ```bash
   python3 --version
   ```

2. **Create a virtual environment**  
   In your project directory, run:
   ```bash
   python3 -m venv venv
   ```
   This creates a folder named `venv` containing the virtual environment.

3. **Activate the virtual environment**  
   - On **macOS/Linux**:
     ```bash
     source venv/bin/activate
     ```

4. **Install project dependencies**  
   Once activated, install dependencies with:
   ```bash
   pip install -r requirements.txt
   ```

5. **Deactivate the virtual environment (when done)**  
   ```bash
   deactivate
   ```