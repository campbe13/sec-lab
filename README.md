# Security lab
You will be running cowrie in a container on your system.  Use ssb and the wordlists in the directory here
to run a brute force password check against your system.

1. on port 8222 (against the honeypot)
2. on port 22 against your sshd

### Install Secure Shell Bruteforcer — A faster & simpler way to bruteforce SSH server.
[ssb](https://github.com/kitabisa/ssb/)
```
```bash
curl -sSfL 'https://git.io/kitabisa-ssb' | sh -s -- -b /usr/local/bin
```

## Usage

```bash
▶ ssb [-p port] [-w wordlist.txt] [-t timeout]
      [-c concurrent] [-r retries] [-o output] [user@]hostname
```

### Options:

```txt
  -p port
     Port to connect to on the remote host (default 22).
  -w wordlist
     Path to wordlist file.
  -t timeout
     Connection timeout (default 30s).
  -c concurrent
     Concurrency/threads level (default 100).
  -r retries
     Specify the connection retries (default 1).
  -o output
     Save valid password to file.
  -v
     Verbose mode.
```

## Refs
* https://github.com/kitabisa/ssb/
* wordlists from https://github.com/1N3/BruteX
