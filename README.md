# Security lab
Do this with a  parter, alternate between each other's systems as attacker. 

You will be running cowrie in a container on your system.  Use the [wordlists](/wordlists) in the directory here
to run a brute force password check against your system.  If you wish you can fetch more with [wordlistctl](https://github.com/BlackArch/wordlistctl)

Use both *hydra* and optionally *ssb* and be sure to run your tests against
1. port 8222 ( the cowrie honeypot)
2. port 22 ( your sshd )

__Note__ with great power comes great responsibility, you must not use these tools against any devices other than your partner's VM [professional conduct](https://www.dawsoncollege.qc.ca/computer-science-technology/professional-conduct/)

## Use hydra
```
apt install hydra
```
First look at the files in [wordlists](/wordlists)  Choose a few to run all of the below tests against sshd & the honeypot.   Before you start add add a couple of the userids you created and their passwords to the files you will use.   

use the verbose option to see more information
### bruteforcing passwords
brute-force ssh passwords with a known username, the syntax is
* `$ hydra -l <username> -P <path to wordlist> <IP> ssh`
### bruteforcing userids
brute-force ssh userids with a known password, the syntax is
* `$ hydra -L <path to wordlist> -p <password> <IP> ssh`
### bruteforcing usernames and passwords
If you do not know  the username and the password, the syntax is as follows:
* `$ hydra -L <path to username wordlist> -P <path to password wordlist> <IP> ssh`
### bruteforcing against the cowrie container
Since you are running the cowrie container also run some tests against it (use the `-s` option to indicate the cowrie port )

#### some hydra options
see also `hydra -h`
```
-l -> Specify a username to use during brute force attack
-L -> Specify a wordlist of usernames to be used during the bruteforce attack
-p -> Specify a password to use during brute force attack
-P -> Specify a wordlist of passwords to be used during the bruteforce attack
-M -> list of IP addresses 
-s -> change the port to use
-V -> verbose output
-e -> extra options, for example n - null, s userid password same, r userid password reversed username
```
## Optional: Use Secure Shell Bruteforcer — A faster & simpler way to bruteforce against an SSH server.
[ssb](https://github.com/kitabisa/ssb/)

```bash
curl -sSfL 'https://git.io/kitabisa-ssb' | sh -s -- -b /usr/local/bin
```
Run at least 1 test against both sshd & the honeypot
First look at the files in [wordlists](/wordlists)  Choose a few to run all of the below tests against sshd & the honeypot.   Before you start add add a couple of the userids you created and their passwords to the files you will use. 

### Usage

```bash
 ssb [-p port] [-w wordlist.txt] [-t timeout]
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
* https://www.linuxfordevices.com/tutorials/linux/hydra-brute-force-ssh
