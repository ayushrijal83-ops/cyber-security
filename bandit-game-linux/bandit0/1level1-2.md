## <span style="font-size: 18px">Bandit Level 1 → 2</span>

**<span style="font-size: 18px">The problem:</span>**<span style="font-size: 18px"> The file was named </span>`-`

**<span style="font-size: 18px">Why</span>** `cat -`<span style="font-size: 18px"> fails: Most commands treat </span>`-`<span style="font-size: 18px"> as a special flag, not a filename. So </span>`cat -`<span style="font-size: 18px"> doesn't read a file — it waits for input from the terminal instead.</span>

**<span style="font-size: 18px">The fix:</span>**<span style="font-size: 18px"> </span>`cat ./-`

- `.`<span style="font-size: 18px"> = the current directory</span>

- `/-`<span style="font-size: 18px"> = the file named </span>`-`<span style="font-size: 18px"> inside it</span>

<span style="font-size: 18px">By writing </span>`./-`<span style="font-size: 18px">, you're telling the shell: </span>*<span style="font-size: 18px">"This is a file path, not a flag."</span>*

**<span style="font-size: 18px">Password for Level 2:</span>**<span style="font-size: 18px"> </span>`PK8fYLZg2hnHSz83plBL1iEPKdD3QToB`

**<span style="font-size: 18px">The lesson:</span>**<span style="font-size: 18px"> When a filename is weird (starts with </span>`-`<span style="font-size: 18px">, contains spaces, etc.), escape it with </span>`./`<span style="font-size: 18px"> or quotes. Never assume normal filenames.</span>

---

<span style="font-size: 18px">Keep this in your notes. You'll see this trick again in later levels and in real engagements.</span>

**<span style="font-size: 18px">Now Level 2 → Level 3.</span>**

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
ssh bandit2@bandit.labs.overthewire.org -p 2220
```