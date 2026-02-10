# vscode-commit-notifier

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D%2014.0.0-blue.svg)](https://nodejs.org/)

A lightweight Node.js utility that monitors your local Git repository and sends a desktop notification when you have reached a specific threshold of changed lines. This tool ensures you commit your work frequently, keeping your Git history clean and manageable.

**Currently only configured for MacOS, but will update later for other systems.**


## Features

* **Real-time Git Diff Tracking**: Calculates the total number of line changes (additions and deletions) in your current working directory.
* **Customizable Threshold**: Automatically triggers a reminder once you exceed a set limit of changed lines (default is 5).
* **Native Desktop Notifications**: Uses `node-notifier` to send cross-platform alerts on macOS, Windows, and Linux.
* **Smart Change Detection**: Includes both staged and unstaged changes using `git diff HEAD --numstat`.
* **VS Code Integration**: Designed to run as a background task within Visual Studio Code.

## Screenshots

![App Screenshot](https://via.placeholder.com/600x400?text=Commit+Reminder+Notification)

## Demo

![App Demo](https://via.placeholder.com/600x400?text=Animated+Demo+Placeholder)

## Tech Stack

* **Runtime**: Node.js
* **Notification Utility**: [node-notifier](https://www.npmjs.com/package/node-notifier)
* **API Interaction**: Git CLI (`child_process`)
* **Version Control**: Git

## NPM References and Dependencies

### Dependencies
* **node-notifier**: A Node.js module for sending notifications on native Mac, Windows, and Linux.

### Dev Dependencies
* **nodemon**: Used to automatically restart the notifier script upon file changes, ensuring continuous monitoring.

## Environment Variables

The current version uses a hardcoded constant for the threshold. However, the script can be modified to support the following:

| Variable | Description | Default |
| :--- | :--- | :--- |
| `COMMIT_THRESHOLD` | The number of changed lines that triggers a notification. | `5` |

## VS Code Task Configuration

The `tasks.json` file is configured to run the script `npm run notify`, found in `package.json` on `folderOpen` to seamlessly start the `commitReminder.js` file as soon as you open your project folder in VS Code. It uses `nodemon` to restart the process on each save in a dedicated terminal panel. Shows the problems panel `onProblem`. 

## Customizable options
* Change the `COMMIT_THRESHOLD` in `commitReminder.js` from the default `5` to any number of lines desired.

* More customizations via `notifier.notify` object in `commitReminder.js` change:
   * `title` or `message` text to preference.

   * `sound` to available system sounds: `Basso`, `Blow`, `Bottle`, `Frog`, `Funk`, `Glass`, `Hero`, `Morse`, `Ping`, `Pop`, `Purr`, `Sosumi`, `Submarine`, & `Tink`
    
    * `wait` (true/false) to wait for user action
    
    * `timeout` (in seconds) to set notification timeout after no user action
    
    * SEE `node-notifier` documentation for more options.


## Run Locally

### Prerequisites
* **Node.js**: Ensure you have Node.js installed on your machine.
* **Git**: Must be installed and initialized within your project folder.

### Setup Instructions
1.  **Clone the repository**
    ```bash
    git clone [https://github.com/your-username/vscode-commit-notifier.git](https://github.com/your-username/vscode-commit-notifier.git)
    ```

2. **Transport folder contents**
    ```bash
    cp -r vscode-commit-notifier/* YOUR_PROJECT_FOLDER/.vscode/
    ```
    
3. **Install dependencies**
    ```bash
    cd YOUR_PROJECT_FOLDER/.vscode/
    npm install
    ```

4.  **Open or Reopen Folder in VS Code**
    * Via file manager
    
    OR
    
    * Via terminal
    ```bash
    code PATH_TO/YOUR_PROJECT_FOLDER
    ```

6.  **Accept "allow automatic tasks to run" Prompt**
    * Click "Allow and run"

6.  **(Optional) Run the script manually**
    ```bash
    node commitReminder.js
    ```

7.  **(Optional) Run the watch script**
    ```bash
    npm run watch-commits
    ```

## License

[MIT](https://opensource.org/licenses/MIT) - Copyright (c) 2026 Kacie Dearman