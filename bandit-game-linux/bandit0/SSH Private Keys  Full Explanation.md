## <span style="font-size: 24px">SSH Private Keys — Full Explanation</span>

### <span style="font-size: 24px">What is SSH?</span>

<span style="font-size: 24px">SSH (Secure Shell) is a protocol for connecting to remote machines securely. Normally, you authenticate with a </span>**<span style="font-size: 24px">username + password</span>**<span style="font-size: 24px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
ssh bandit13@bandit.labs.overthewire.org -p 2220
Password: ********
```

<span style="font-size: 24px">But there's a second, more secure method: </span>**<span style="font-size: 24px">key-based authentication</span>**<span style="font-size: 24px">.</span>

---

### <span style="font-size: 24px">How Key-Based Authentication Works</span>

<span style="font-size: 24px">SSH uses </span>**<span style="font-size: 24px">public-key cryptography</span>**<span style="font-size: 24px">. It works in pairs:</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Key</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it is</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Where it lives</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><strong><span style="font-size: 24px">Private key</span></strong></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Your secret. Never share it.</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Stays on your machine</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong><span style="font-size: 24px">Public key</span></strong></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Derived from the private key. Can be shared freely.</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Stored on the server</span></p></td></tr></tbody>
</table>

<span style="font-size: 24px">Think of it like a lock and key:</span>

- <span style="font-size: 24px">The </span>**<span style="font-size: 24px">public key</span>**<span style="font-size: 24px"> is the lock (installed on the server)</span>

- <span style="font-size: 24px">The </span>**<span style="font-size: 24px">private key</span>**<span style="font-size: 24px"> is the physical key (held by you)</span>

<span style="font-size: 24px">When you connect, the server challenges you: </span>*<span style="font-size: 24px">"Prove you have the matching private key."</span>*<span style="font-size: 24px"> If you do, you're in. No password needed.</span>

---

### <span style="font-size: 24px">Why Private Keys Are Better Than Passwords</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Feature</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Password</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Private Key</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Length</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Usually 8-20 characters</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">2048+ bits (hundreds of characters)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Brute-forceable?</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Yes, often</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Practically impossible</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Can be shared safely?</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">No</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Private key never shared, public key can be</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Used in automation?</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Hard</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Easy (scripts, tools, CI/CD)</span></p></td></tr></tbody>
</table>

---

### <span style="font-size: 24px">The </span>`-i`<span style="font-size: 24px"> Flag</span>

<span style="font-size: 24px">The </span>`-i`<span style="font-size: 24px"> flag tells SSH:</span>

> *<span style="font-size: 24px">"Use this file as my private key for authentication, instead of asking for a password."</span>*

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Part</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">ssh</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">The SSH command</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-i sshkey.private</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Use this private key file</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">bandit14@...</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Username and host to connect to</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-p 2220</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Port number</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">SCP — Secure Copy Protocol</span>

### <span style="font-size: 24px">What is SCP?</span>

<span style="font-size: 24px">SCP (Secure Copy) is a tool for </span>**<span style="font-size: 24px">transferring files</span>**<span style="font-size: 24px"> between machines over SSH. It uses the same security as SSH — all data is encrypted.</span>

### <span style="font-size: 24px">Basic Syntax</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
scp [options] source destination
```

<span style="font-size: 24px">Where </span>`source`<span style="font-size: 24px"> and </span>`destination`<span style="font-size: 24px"> can be:</span>

- <span style="font-size: 24px">Local files: </span>`./file.txt`

- <span style="font-size: 24px">Remote files: </span>`user@host:path/to/file`

---

### <span style="font-size: 24px">How I Used It</span>

<span style="font-size: 24px">I needed to download the private key from the Bandit server to my local Windows machine.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./sshkey.private
```

<span style="font-size: 24px">Breaking it down:</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Part</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">scp</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Secure copy command</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-P 2220</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Port 2220 (note: capital P for SCP, lowercase p for SSH)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">bandit13@bandit.labs.overthewire.org:sshkey.private</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Source: the file on the remote server</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">./sshkey.private</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Destination: save it in my current directory with the same name</span></p></td></tr></tbody>
</table>

---

### <span style="font-size: 24px">Important: </span>`-P`<span style="font-size: 24px"> vs </span>`-p`

<span style="font-size: 24px">This confuses everyone:</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Flag</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Meaning</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">ssh</code></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-p 2220</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">lowercase p = port</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">scp</code></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-P 2220</code></p></td><td colspan="1" rowspan="1"><p><strong><span style="font-size: 24px">capital P</span></strong><span style="font-size: 24px"> = port</span></p></td></tr></tbody>
</table>

<span style="font-size: 24px">Why the difference? Because in SCP, lowercase </span>`-p`<span style="font-size: 24px"> means </span>**<span style="font-size: 24px">preserve file timestamps</span>**<span style="font-size: 24px">, not port. So SCP uses capital </span>`-P`<span style="font-size: 24px"> for port.</span>

---

### <span style="font-size: 24px">Download vs Upload with SCP</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Task</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Download from remote to local</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">scp -P 2220 user@host:remote/file ./local/</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Upload from local to remote</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">scp -P 2220 ./local/file user@host:remote/</code></p></td></tr></tbody>
</table>

<span style="font-size: 24px">Mnemonic: </span>**<span style="font-size: 24px">Source first, destination second.</span>**<span style="font-size: 24px"> Always.</span>

---

## <span style="font-size: 24px">The Complete Flow I Used</span>

### <span style="font-size: 24px">Step 1: Found the key on the server</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
ls -la
```

<span style="font-size: 24px">→ saw </span>`sshkey.private`

### <span style="font-size: 24px">Step 2: Tried to use it from inside the server (failed)</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
ssh -i sshkey.private bandit14@localhost -p 2220
```

<span style="font-size: 24px">→ Blocked: SSH from localhost is disabled</span>

### <span style="font-size: 24px">Step 3: Read the HINT</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
cat HINT
```

<span style="font-size: 24px">→ "Log out and log in again"</span>

### <span style="font-size: 24px">Step 4: Exited the server</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
exit
```

<span style="font-size: 24px">→ Back to my local Windows PowerShell</span>

### <span style="font-size: 24px">Step 5: Downloaded the key</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
scp -P 2220 bandit13@bandit.labs.overthewire.org:sshkey.private ./sshkey.private
```

### <span style="font-size: 24px">Step 6: Used the key to connect as bandit14</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

### <span style="font-size: 24px">Step 7: Read the password</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
cat /etc/bandit_pass/bandit14
```

---

## <span style="font-size: 24px">Key Takeaways</span>

1. **<span style="font-size: 24px">Private key = password replacement.</span>**<span style="font-size: 24px"> Use </span>`-i`<span style="font-size: 24px"> to specify it.</span>

2. **<span style="font-size: 24px">SCP = file transfer over SSH.</span>**<span style="font-size: 24px"> Use capital </span>`-P`<span style="font-size: 24px"> for port.</span>

3. **<span style="font-size: 24px">Source first, destination second</span>**<span style="font-size: 24px"> in SCP.</span>

4. **<span style="font-size: 24px">If the server blocks localhost, exit and connect from outside.</span>**

5. **<span style="font-size: 24px">Read the HINT file.</span>**<span style="font-size: 24px"> It usually tells you exactly what to do.</span>