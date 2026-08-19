## <span style="font-size: 24px">What is Base64?</span>

<span style="font-size: 24px">Base64 is a way of </span>**<span style="font-size: 24px">encoding data</span>**<span style="font-size: 24px"> — converting any type of data (text, binary, images, anything) into a string of </span>**<span style="font-size: 24px">only 64 safe characters</span>**<span style="font-size: 24px">:</span>

- <span style="font-size: 24px">Uppercase letters: </span>`A-Z`<span style="font-size: 24px"> (26)</span>

- <span style="font-size: 24px">Lowercase letters: </span>`a-z`<span style="font-size: 24px"> (26)</span>

- <span style="font-size: 24px">Numbers: </span>`0-9`<span style="font-size: 24px"> (10)</span>

- <span style="font-size: 24px">Two symbols: </span>`+`<span style="font-size: 24px"> and </span>`/`<span style="font-size: 24px"> (2)</span>

<span style="font-size: 24px">That's 64 characters total — hence the name </span>**<span style="font-size: 24px">Base64</span>**<span style="font-size: 24px">.</span>

---

## <span style="font-size: 24px">Why does Base64 exist?</span>

<span style="font-size: 24px">Computers store data in </span>**<span style="font-size: 24px">binary</span>**<span style="font-size: 24px"> (0s and 1s). But many systems — like email, web pages, URLs, and text files — can only handle </span>**<span style="font-size: 24px">plain text</span>**<span style="font-size: 24px"> safely.</span>

<span style="font-size: 24px">The problem: binary data contains characters that break text-based systems (null bytes, control characters, special symbols).</span>

<span style="font-size: 24px">Base64 solves this by taking any data and converting it into </span>**<span style="font-size: 24px">safe, printable text</span>**<span style="font-size: 24px"> that can travel anywhere without breaking.</span>

<span style="font-size: 24px">Think of it like translating a secret message into a language that everyone can read — then translating it back when it reaches the destination.</span>

---

## <span style="font-size: 24px">How it works (the simple version)</span>

<span style="font-size: 24px">Base64 takes your data in chunks of </span>**<span style="font-size: 24px">3 bytes</span>**<span style="font-size: 24px"> (24 bits) and splits them into </span>**<span style="font-size: 24px">4 groups of 6 bits</span>**<span style="font-size: 24px"> each.</span>

<span style="font-size: 24px">Each 6-bit group maps to one of the 64 characters.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
Original data:  "Hi"
Binary:          01001000 01101001

Split into 6-bit groups:
010010 → S
000110 → G
1001?? → (padding needed)

Result:  "SGk="
```

<span style="font-size: 24px">The </span>`=`<span style="font-size: 24px"> at the end is </span>**<span style="font-size: 24px">padding</span>**<span style="font-size: 24px"> — it's added when the data doesn't split evenly into 3-byte chunks.</span>

---

## <span style="font-size: 24px">Example: Encode "Hello"</span>

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
echo -n "Hello" | base64
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
SGVsbG8=
```

<span style="font-size: 24px">So </span>`Hello`<span style="font-size: 24px"> becomes </span>`SGVsbG8=`<span style="font-size: 24px"> in Base64.</span>

<span style="font-size: 24px">Notice the </span>`=`<span style="font-size: 24px"> at the end — that's padding because "Hello" is 5 characters, not a multiple of 3.</span>

---

## <span style="font-size: 24px">Example: Decode "SGVsbG8="</span>

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
echo -n "SGVsbG8=" | base64 -d
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
Hello
```

<span style="font-size: 24px">The </span>`-d`<span style="font-size: 24px"> flag means </span>**<span style="font-size: 24px">decode</span>**<span style="font-size: 24px"> — turn Base64 back into original data.</span>

---

## <span style="font-size: 24px">The </span>`base64`<span style="font-size: 24px"> command in Linux</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">base64 file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Encode a file into Base64</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">base64 -d file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Decode a Base64 file back to original</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">echo -n "text" | base64</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Encode a string</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">echo -n "encoded" | base64 -d</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Decode a string</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">How to recognize Base64</span>

<span style="font-size: 24px">Base64 strings look like random text made of:</span>

- <span style="font-size: 24px">Letters (upper and lowercase)</span>

- <span style="font-size: 24px">Numbers</span>

- `+`<span style="font-size: 24px"> and </span>`/`

- <span style="font-size: 24px">Often ends with </span>`=`<span style="font-size: 24px"> or </span>`==`<span style="font-size: 24px"> (padding)</span>

<span style="font-size: 24px">Examples:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
SGVsbG8=
dXNlcjpwYXNzd29yZA==
aGVsbG8gd29ybGQ=
```

<span style="font-size: 24px">If you see a string that looks like a jumble of letters and numbers ending with </span>`=`<span style="font-size: 24px">, it's probably Base64.</span>

---

## <span style="font-size: 24px">Where you'll see Base64 in hacking</span>

### <span style="font-size: 24px">1. Web applications</span>

<span style="font-size: 24px">Cookies, session tokens, and auth data are often Base64-encoded.</span>

### <span style="font-size: 24px">2. CTF challenges</span>

<span style="font-size: 24px">Flags and passwords are frequently encoded in Base64.</span>

### <span style="font-size: 24px">3. Data exfiltration</span>

<span style="font-size: 24px">Attackers encode stolen data in Base64 to hide it from simple detection.</span>

### <span style="font-size: 24px">4. File transfers</span>

<span style="font-size: 24px">Binary files are converted to Base64 for safe transfer through text-only channels.</span>

### <span style="font-size: 24px">5. JWTs (JSON Web Tokens)</span>

<span style="font-size: 24px">Authentication tokens are Base64-encoded JSON.</span>

---

## <span style="font-size: 24px">Base64 vs Encryption (important!)</span>

**<span style="font-size: 24px">Base64 is NOT encryption.</span>**<span style="font-size: 24px"> It's just encoding. Anyone can decode it instantly.</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Feature</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Base64</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Encryption</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Purpose</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Make data safe for text systems</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Keep data secret</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Key needed?</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">No</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Yes</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Reversible?</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Instantly, by anyone</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Only with the key</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Security</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Zero</span></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Strong (if done right)</span></p></td></tr></tbody>
</table>

<span style="font-size: 24px">If you see Base64 on a website and think "I found the password," you're wrong — it's encoded, not protected. You can decode it in one command.</span>

---

## <span style="font-size: 24px">Quick Reference</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Task</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Encode string</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">echo -n "hello" | base64</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Decode string</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">echo -n "aGVsbG8=" | base64 -d</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Encode file</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">base64 file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Decode file</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">base64 -d file.txt</code></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">The mental model</span>

> **<span style="font-size: 24px">Base64 = translating data into a safe alphabet. It's not hiding anything — it's just changing the language.</span>**

<span style="font-size: 24px">When you see </span>`=`<span style="font-size: 24px"> at the end of a random-looking string, think Base64. Then decode it. One command and you're done.</span>

---

<span style="font-size: 24px">Now you're ready for </span>**<span style="font-size: 24px">Bandit Level 10 → 11</span>**<span style="font-size: 24px">. The password in </span>`data.txt`<span style="font-size: 24px"> is Base64-encoded. All you need is:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
base64 -d data.txt
```

<span style="font-size: 24px">Or:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
cat data.txt | base64 -d
```

<span style="font-size: 24px">Go. What do you get?</span>