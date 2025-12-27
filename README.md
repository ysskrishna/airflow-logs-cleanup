# Airflow Logs Cleanup

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Python](https://img.shields.io/badge/python-3.8%2B-blue.svg)

A lightweight solution to automatically clean up old Airflow log files, helping you save disk space and keep your Airflow environment tidy. This repository provides both a standalone script and an Airflow DAG for automated log cleanup.

## Why Airflow Logs Cleanup?

Airflow generates a large volume of log files over time, which can quickly consume disk space. Manually cleaning these logs is tedious and error-prone. This tool automates the process by:

- **Preventing disk space issues**: Automatically removes old logs before they fill up your disk
- **Reducing maintenance overhead**: Set it and forget it with the included Airflow DAG
- **Keeping your environment clean**: Removes rotated logs and empty directories automatically
- **Configurable retention**: Adjust how long to keep logs based on your needs

## Features

- **Deletes rotated `dag_processor_manager` logs** (e.g., `dag_processor_manager.log.1`, `.2`, etc.)
- **Removes log files older than 7 days** (configurable)
- **Cleans up empty directories** left after log deletion
- **Can be run as a standalone script or as an Airflow DAG**
- **Safe and reliable**: Includes error handling for file operations

## Requirements

- Python 3.8+
- Apache Airflow (any version that supports PythonOperator)
- `AIRFLOW_HOME` environment variable must be set

## Usage

### Option 1: Standalone Script

You can run `cleanup_logs.py` directly to clean up logs:

```bash
python cleanup_logs.py
```

**Note:** The `AIRFLOW_HOME` environment variable must be set to your Airflow home directory.

### Option 2: Airflow DAG (Recommended)

The `cleanup_logs_dag.py` file defines a DAG that runs the cleanup task daily at 3 AM.

**Setup Steps:**
1. Copy `cleanup_logs_dag.py` to your Airflow DAGs folder (typically `$AIRFLOW_HOME/dags/`)
2. Ensure the `AIRFLOW_HOME` environment variable is set for your Airflow environment
3. The DAG will appear in the Airflow UI as `cleanup_logs_dag`
4. Enable the DAG in the Airflow UI to start automatic cleanup

**DAG Schedule:** Daily at 3:00 AM (configurable in the DAG definition)

## Configuration

### Retention Period

By default, logs older than **7 days** are deleted. You can change this by modifying the `MILLISECONDS_TO_KEEP` constant in the scripts:

```python
# In cleanup_logs.py or cleanup_logs_dag.py
MILLISECONDS_TO_KEEP = 7 * 86400 * 1000  # 7 days in milliseconds

# Example: Change to 14 days
MILLISECONDS_TO_KEEP = 14 * 86400 * 1000  # 14 days
```

### DAG Schedule

To change when the cleanup runs, modify the `schedule_interval` in `cleanup_logs_dag.py`:

```python
# Current: Daily at 3 AM
schedule_interval="0 3 * * *"

# Example: Daily at midnight
schedule_interval="0 0 * * *"

# Example: Weekly on Sundays at 2 AM
schedule_interval="0 2 * * 0"
```

## How It Works

1. **Rotated Log Cleanup**: Identifies and deletes rotated `dag_processor_manager` logs (`.log.1`, `.log.2`, etc.)
2. **Old File Cleanup**: Recursively scans the logs directory and removes files older than the retention period
3. **Empty Directory Cleanup**: Removes directories that become empty after file deletion (excluding `dag_processor_manager`)

## Error Handling

The script includes error handling for:
- Missing directories
- Permission errors
- File system errors
- Missing `AIRFLOW_HOME` environment variable

All errors are logged to the console without stopping the cleanup process.


## Contributing

Contributions are welcome! If you have ideas for improvements, bug fixes, or new features, please feel free to submit a pull request or open an issue.

## Support

If you find this useful, please consider:

- ⭐ **Starring** the repository on GitHub to help others discover it.
- 💖 **Sponsoring** to support ongoing maintenance and development.

[Become a Sponsor on GitHub](https://github.com/sponsors/ysskrishna) | [Support on Patreon](https://patreon.com/ysskrishna)

## License

MIT License - see the [LICENSE](LICENSE) file for details.

## Author

**Y. Siva Sai Krishna**

- GitHub: [@ysskrishna](https://github.com/ysskrishna)
- LinkedIn: [ysskrishna](https://linkedin.com/in/ysskrishna) 