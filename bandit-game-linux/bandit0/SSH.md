## <span style="font-size: 18px">Bandit Level 0 → 1</span>

**<span style="font-size: 18px">What I learned: SSH basics</span>**

<span style="font-size: 18px">SSH connects you to a remote machine. The command has three parts:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
ssh username@hostname -p port
```

- `username`<span style="font-size: 18px"> = the account on the remote server you're logging into</span>

- `hostname`<span style="font-size: 18px"> = the server's address</span>

- `-p`<span style="font-size: 18px"> = the port SSH is running on (default is 22; Bandit uses 2220)</span>

<span style="font-size: 18px">So for Bandit:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

<span style="font-size: 18px">That means: </span>*<span style="font-size: 18px">"Connect to the server</span>* `bandit.labs.overthewire.org`<span style="font-size: 18px"> on port 2220, and log in as the user </span>`bandit0`<span style="font-size: 18px">."</span>

**<span style="font-size: 18px">How I found the password:</span>**

1. `ls`<span style="font-size: 18px"> — listed the files in the current directory</span>

2. <span style="font-size: 18px">Found a file called </span>`readme`

3. `cat readme`<span style="font-size: 18px"> — printed its contents</span>

4. <span style="font-size: 18px">That was the password for level 1</span>

**<span style="font-size: 18px">Password for Level 1:</span>**<span style="font-size: 18px"> </span>`6y2kwnwK6grgvwvpvLaa2T1cpFEKOhNR`

**<span style="font-size: 18px">The loop:</span>**<span style="font-size: 18px"> </span>`ls`<span style="font-size: 18px"> to see what's there → </span>`cat`<span style="font-size: 18px"> to read what's inside → found the password. Enumeration first, always.</span>