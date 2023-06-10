# Using TMUX

`tmux` is a terminal multiplexer that allows you to manage multiple terminal sessions within a single window. It's useful for running long-running processes, managing remote sessions, or simply organizing your terminal workspaces. Here's a basic guide to get started with `tmux`.

1. Install `tmux`:
   Depending on your operating system, use the appropriate package manager to install `tmux`.

   - For Ubuntu/Debian:
     ```
     sudo apt-get update
     sudo apt-get install tmux
     ```

   - For CentOS/RHEL:
     ```
     sudo yum install tmux
     ```

   - For macOS (using Homebrew):
     ```
     brew install tmux
     ```

2. Start a new `tmux` session:
   To start a new session, simply type `tmux` in your terminal and hit enter. You'll notice a green status bar at the bottom of your terminal window, which indicates that you're inside a `tmux` session.

3. Basic `tmux` commands:
   `tmux` uses a command prefix, which by default is `Ctrl-b`. To issue a command, press the prefix followed by the desired command key. Some common commands are:

   - Create a new window:
     ```
     Ctrl-b c
     ```

   - Switch to the next window:
     ```
     Ctrl-b n
     ```

   - Switch to the previous window:
     ```
     Ctrl-b p
     ```

   - Rename a window:
     ```
     Ctrl-b ,
     ```

   - Split the current window vertically:
     ```
     Ctrl-b %
     ```

   - Split the current window horizontally:
     ```
     Ctrl-b "
     ```

   - Navigate between panes:
     ```
     Ctrl-b <arrow keys>
     ```

   - Resize panes:
     ```
     Ctrl-b :resize-pane -<direction> <number>
     ```
     (Replace `<direction>` with `U`, `D`, `L`, or `R` for up, down, left, or right, and `<number>` with the number of lines or columns to resize.)

   - Close the current pane:
     ```
     Ctrl-b x
     ```

   - Detach from the current session:
     ```
     Ctrl-b d
     ```

4. Managing sessions:
   - Create a new named session:
     ```
     tmux new-session -s <session-name>
     ```

   - Attach to an existing session:
     ```
     tmux attach-session -t <session-name>
     ```

   - List all sessions:
     ```
     tmux list-sessions
     ```

   - Kill a specific session:
     ```
     tmux kill-session -t <session-name>
     ```

5. Customizing `tmux`:
   You can customize `tmux` by creating a configuration file in your home directory called `.tmux.conf`. This file allows you to set various options, change the key bindings, or modify the appearance of the status bar.

That's a basic introduction to using `tmux`. There are many more advanced features and customizations available, so you might want to check the man page (`man tmux`) or refer to online resources for more information.
