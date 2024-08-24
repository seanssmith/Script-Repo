# Master Script Repository

This repository contains the `master.sh` script, designed to simplify the execution of other scripts stored in a GitHub repository. The `master.sh` script automatically fetches a list of available scripts, allows you to select and run them, and handles dependencies and cleanup. This guide explains how to use the `master.sh` script, its key features, and how to contribute.

The goal of the repo is to make is as simple as possible to run scripts that are stored in a GitHub Repo.

## Table of Contents

- [Usage](#usage)
- [Features](#features)
- [Dependencies](#dependencies)
- [Error Handling](#error-handling)
- [Cleanup](#cleanup)
- [Contributing](#contributing)
- [License](#license)

## Usage

To use the `master.sh` script, run the following command:

```bash
wget https://raw.githubusercontent.com/seanssmith/Script-Repo/main/master.sh -O master.sh && bash master.sh
```

### Example

```bash
wget https://raw.githubusercontent.com/seanssmith/Script-Repo/main/master.sh -O master.sh && bash master.sh
```

```bash
<details>
  <summary>Script Output</summary>


Fetching list of available scripts from GitHub repository...

Available scripts:
1) Bootstrap		     3) Testing/test.sh		  5) script-template.sh
2) Scripts/lxc-bootstrap.sh  4) master.sh		  6) Quit
#? 3

Function: Example Function 1 - Status: Finished ✔
Output:
This is example function 1. ✔

Function: Example Function 2 - Status: Finished ✔
Output:
This is example function 2.
Done ✔

Function: Example Function 3 - Status: Error ✘
Output:
This is example function 3 and it will fail. ✘

Cleaned up ✔
Function: Test Reconfiguring - Status: Running...
Question? (y/n): t
Invalid choice.
Question? (y/n): y
Function: Test Reconfiguring - Status: Finished ✔

Function: Cleaning up - Status: Finished ✔
Output:
Deleted master script...
Cleaned up ✔


Test Script encountered errors!


Script interrupted or an error occurred
Would you like to run more scripts? (y/n)


</details>
```


### Running with Verbose Output

If you want to see more detailed output during execution, use the -v flag:

```bash
bash master.sh -v
```

### Selecting and Running Scripts

1. Fetch List of Scripts: The script automatically fetches the list of available scripts from this repository.
2. Select a Script: You will be prompted to select a script to run from the list of available scripts.
3. Run the Script: The selected script is downloaded, executed, and then cleaned up after execution.


## Features

- Automatic Dependency Installation: Ensures that required tools like sudo, curl, and jq are installed before proceeding.
- Script Fetching and Execution: Automatically retrieves available scripts from the repository and allows for easy selection and execution.
- Verbose Mode: Use the `-v` flag to enable detailed logging during script execution.
- Error Handling: Built-in error handling ensures that the script exits gracefully and provides informative error messages.
- Cleanup: Automatically removes temporary files and the script itself after execution.


## Dependencies

The `master.sh` script relies on the following tools:

- `sudo`: Ensures elevated permissions for installing packages and running scripts.
- `curl`: Used to fetch the list of scripts and download individual scripts.
- `jq`: Parses JSON responses from GitHub API.
If any of these tools are not installed, the script will attempt to install them automatically.

The script also uses `task_formatter.sh`, which can be found at the [TaskFormatter Repo](https://github.com/seanssmith/TaskFormatter/blob/main/bash_task_formatter/task_formatter.sh), to format the output of the master script in a better looking way. 

## Error Handling

The script includes robust error handling mechanisms:

- Command Failures: If a command fails (e.g., network issues, missing dependencies), the script will output an error message and exit.
- Invalid Script Selection: If an invalid selection is made, the script will prompt you to try again.
- HTTP Status Codes: When downloading a script, the script checks the HTTP status code and provides feedback if the download fails.

## Cleanup

After running the selected script(s), the master.sh script performs the following cleanup actions:

- Temporary Files: Removes any temporary files created during script execution.
- Self-Removal: Deletes the `master.sh` script itself and the `task_formatter.sh` script used for output formatting.
- These actions ensure that your system remains clean after script execution.

## Contributing

We welcome contributions to this repository! To contribute:

- Fork the repository.
- Create a new branch with your feature or bugfix.
- Submit a pull request for review.

### Adding New Scripts
To add a new script to the repository:

1. Add your script to the repository, ensuring it follows the naming convention (.sh extension).
2. Ensure the script is executable (`chmod +x script_name.sh`).
3. Submit a pull request with your new script.

## Reporting Issues
If you encounter any issues with the `master.sh` script, please open an issue in this repository, providing details about the problem and any relevant logs or error messages.

## License

This repository is licensed under the MIT License. See the LICENSE file for more details.