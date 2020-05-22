# Gemini Server Diagnostics

A diagnostic tool for [gemini](https://portal.mozz.us/gemini/gemini.circumlunar.space/) servers.

## Requirements

Python 3.7 or higher.

Tests that inspect TLS certificates require the [cryptography](https://cryptography.io/en/latest/installation/) library be installed.

## History

This script was born out of discussions on the [gemini mailing list](https://lists.orbitalfox.eu/listinfo/gemini) that it would be useful to have a gemini server "torture test" to uncover bugs and unhandled edge cases in new server implementations. It was originally called "jetforce-diagnostics" and was bundled in with the [jetforce](https://github.com/michael-lazar/jetforce) gemini server. It has now been moved to its own repository and operates as a separate project.

## Usage

```bash
usage: gemini-diagnostics [host] [port] [--help]

A diagnostic tool for gemini servers.

This program will barrage your server with a series of requests in
an attempt to uncover unexpected behavior. Not all of these checks
adhere strictly to the gemini specification. Some of them are
general best practices, and some trigger undefined behavior. Results
should be taken with a grain of salt and analyzed on their own merit.

positional arguments:
  host             server hostname (default: localhost)
  port             server port (default: 1965)

optional arguments:
  -h, --help       show this help message and exit
  --checks CHECKS  comma separated list of checks to apply
  --show-checks    display the complete list of checks and exit
  --delay DELAY    seconds to sleep between checks (default: 2)
```
