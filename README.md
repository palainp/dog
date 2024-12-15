# Dog CLI Tool

`dog` is a command-line tool that captures the current terminal content and saves it to a file. It mimics the opposite behavior of the `cat` command, which displays file content, by capturing the terminal output.
This tool currently only supports `screen` and `tmux` as terminal emulators.

## Features

- **Capture terminal content**: Capture the current visible terminal content and save it to a file.
- **Scrollback buffer support**: Supports capturing the scrollback buffer content from tmux or screen sessions.
- **Options**:
  - `-q` / `--quiet`: Do not print anything except the error messages.
  - `-a` / `--append`: Append the content to an existing file.
  - `-n` / `--number`: Prefix lines with the line number.
  - `-l` / `--length`: Limit the number of lines captured from the terminal history. Default value is the visible space. 0 stands for the entire scrollback buffer.
  
## Installation

You can use it directly from the source.

## Usage

Capture the current visible content of the terminal and save it to a file:

```bash
$ dog output.txt
Detected screen. Capturing 20 lines from scrollback...
Saving to file: output.txt
Content successfully saved to output.txt
```

Append the terminal content to an existing file:

```bash
$ dog -a output.txt
Detected screen. Capturing 20 lines from scrollback...
Appending to file: output.txt
Content successfully saved to output.txt
```

Add line numbers to each line of the captured content:

```bash
$ dog -n output.txt && cat output.txt
Detected screen. Capturing 20 lines from scrollback...
Saving to file: output.txt
Content successfully saved to output.txt
1: Line 1
2: Line 2
...
```

Capture only the last N lines from the terminal's history:

```bash
$ dog -l 50 output.txt
Detected screen. Capturing 50 lines from scrollback...
Saving to file: output.txt
Content successfully saved to output.txt
```

## Requirements

- tmux (optional): For capturing the scrollback buffer in tmux sessions.
- screen (optional): For capturing the scrollback buffer in screen sessions.
- Python 3.x: Required to run the Python script (if not installed globally).
