# Contributing to Airflow Logs Cleanup

Thank you for your interest in contributing to Airflow Logs Cleanup! This document provides guidelines and instructions for contributing to the project.

## How to Contribute

There are many ways to contribute to this project:

- **Report bugs**: If you find a bug, please open an issue describing the problem
- **Suggest features**: Have an idea for a new feature? Open an issue to discuss it
- **Submit pull requests**: Fix bugs, add features, or improve documentation
- **Improve documentation**: Help make the project more accessible to others
- **Share feedback**: Let us know what you think about the project

## Getting Started

### Prerequisites

- Python 3.8 or higher
- Git
- Apache Airflow (for testing DAG functionality)
- `AIRFLOW_HOME` environment variable set (for local testing)

### Development Setup

1. **Fork the repository** on GitHub

2. **Clone your fork**:
   ```bash
   git clone https://github.com/YOUR_USERNAME/airflow-logs-cleanup.git
   cd airflow-logs-cleanup
   ```

3. **Set up your environment**:
   ```bash
   # Ensure AIRFLOW_HOME is set
   export AIRFLOW_HOME=/path/to/your/airflow/home
   ```

4. **Test the current code**:
   ```bash
   python cleanup_logs.py
   ```

## Development Guidelines

### Code Style

- Follow **PEP 8** style guidelines for Python code
- Use meaningful variable and function names
- Add docstrings to functions and classes
- Keep functions focused and single-purpose
- Maximum line length: 88 characters (Black formatter default)

### Code Formatting

We recommend using:
- **Black** for code formatting
- **flake8** or **pylint** for linting

Example:
```bash
# Install formatting tools (optional but recommended)
pip install black flake8

# Format code
black cleanup_logs.py cleanup_logs_dag.py

# Check for linting issues
flake8 cleanup_logs.py cleanup_logs_dag.py
```

### Commit Messages

Write clear and descriptive commit messages:

- Use the present tense ("Add feature" not "Added feature")
- Use the imperative mood ("Move cursor to..." not "Moves cursor to...")
- Limit the first line to 72 characters or less
- Reference issues and pull requests liberally after the first line

Examples:
```
Add support for custom retention periods

Allow users to specify retention period via environment variable
Fixes #123
```

```
Fix error handling for missing log directories

Previously, the script would crash if the logs directory didn't exist.
Now it gracefully handles this case and logs a warning.
```

## Pull Request Process

1. **Create a branch** for your changes:
   ```bash
   git checkout -b feature/your-feature-name
   # or
   git checkout -b fix/your-bug-fix
   ```

2. **Make your changes**:
   - Write clean, readable code
   - Add comments where necessary
   - Update documentation if needed
   - Test your changes thoroughly

3. **Test your changes**:
   - Run the standalone script to ensure it works
   - If modifying the DAG, test it in an Airflow environment
   - Verify error handling works correctly

4. **Commit your changes**:
   ```bash
   git add .
   git commit -m "Your descriptive commit message"
   ```

5. **Push to your fork**:
   ```bash
   git push origin feature/your-feature-name
   ```

6. **Open a Pull Request**:
   - Go to the original repository on GitHub
   - Click "New Pull Request"
   - Select your branch
   - Fill out the PR template (if available)
   - Describe your changes clearly

### Pull Request Guidelines

- **Keep PRs focused**: One feature or bug fix per PR
- **Update documentation**: If you add features, update the README.md
- **Add tests if applicable**: While not required, tests are appreciated
- **Respond to feedback**: Be open to suggestions and make requested changes
- **Keep PRs up to date**: Rebase or merge main branch if there are conflicts

## Reporting Issues

When reporting bugs or requesting features, please include:

### For Bug Reports:
- **Description**: Clear description of the bug
- **Steps to reproduce**: Detailed steps to reproduce the issue
- **Expected behavior**: What you expected to happen
- **Actual behavior**: What actually happened
- **Environment**: 
  - Python version
  - Airflow version (if applicable)
  - Operating system
  - `AIRFLOW_HOME` path
- **Error messages**: Full error messages or stack traces
- **Screenshots**: If applicable

### For Feature Requests:
- **Description**: Clear description of the feature
- **Use case**: Why this feature would be useful
- **Proposed solution**: How you envision it working (optional)
- **Alternatives**: Other solutions you've considered (optional)

## Testing

While automated tests are not currently in place, please test your changes manually:

1. **Test the standalone script**:
   ```bash
   python cleanup_logs.py
   ```

2. **Test the DAG** (if modified):
   - Copy to your Airflow DAGs folder
   - Enable and trigger the DAG in Airflow UI
   - Verify it runs successfully

3. **Test edge cases**:
   - Missing `AIRFLOW_HOME` environment variable
   - Non-existent log directories
   - Permission errors
   - Empty log directories

## Areas for Contribution

We welcome contributions in these areas:

- **Bug fixes**: Fix any issues you encounter
- **Performance improvements**: Optimize file operations
- **New features**: 
  - Support for different log retention strategies
  - Configuration via config files
  - Dry-run mode
  - Logging improvements
- **Documentation**: 
  - Improve README
  - Add code comments
  - Create tutorials or guides
- **Testing**: Add unit tests or integration tests
- **Code quality**: Refactor for better maintainability

## Questions?

If you have questions about contributing, feel free to:
- Open an issue with the `question` label
- Reach out to the maintainer

## Code of Conduct

- Be respectful and inclusive
- Welcome newcomers and help them get started
- Focus on constructive feedback
- Respect different viewpoints and experiences

## License

By contributing, you agree that your contributions will be licensed under the MIT License.

---

Thank you for contributing to Airflow Logs Cleanup! 🎉

