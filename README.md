![Banner](banner.png)

# file-content-sanitizer
Removes or redacts sensitive data patterns (e.g., credit card numbers, email addresses, social security numbers) from a file, based on configurable regular expressions or predefined data type definitions. - Focused on File operations and analysis

## Install
`git clone https://github.com/ShadowStrikeHQ/file-content-sanitizer`

## Usage
`./file-content-sanitizer [params]`

## Parameters
- `-h`: Show help message and exit
- `--patterns`: Regular expression patterns to sanitize. When supplied, these replace the default patterns. When omitted, the default patterns are used.
- `--redact`: Replace matched patterns with `[REDACTED]`. If not set, matches are removed.
- `--log_level`: Set the logging level (default: INFO)

## Notes
- With no `--patterns`, the default pattern set runs: credit card numbers, email addresses, and social security numbers. A run with `--patterns` uses only the patterns supplied, replacing the defaults.
- The output file must not be the input file. A run whose output path resolves to the input file is refused at exit 1, including the same path written with a `./` prefix or through a symlink.
- Redactions are counted and the count is logged. A run that matches nothing, and an empty input run, exit 1 with a plain line, write no output file, and do not print a Successfully sanitized line.
- An invalid regular expression exits 1 with no output written.

## License
Copyright (c) ShadowStrikeHQ
