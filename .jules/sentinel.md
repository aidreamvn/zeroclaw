## 2025-05-14 - Command Argument Path Escape
**Vulnerability:** Workspace isolation bypass via command arguments. Allowed commands like `ls`, `cat`, or `find` could be used to access absolute or forbidden paths (e.g., `ls /etc`) because only the base command was validated, not its arguments.
**Learning:** Security allowlists often focus on the "what" (command) but miss the "where" (arguments). In a trait-based architecture, validation must be applied consistently across all tools that take path-like inputs, whether they are direct file tools or shell commands.
**Prevention:** Implement argument-level path validation in the security policy. Every word in a shell command that looks like a path should be passed through the same `is_path_allowed` check used by file-system tools.
