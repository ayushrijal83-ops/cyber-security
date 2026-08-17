## <span style="font-size: 24px">Bandit Level 7 → 8</span>

**<span style="font-size: 24px">The challenge:</span>**<span style="font-size: 24px"> The password is stored in </span>`data.txt`<span style="font-size: 24px">, next to the word </span>`millionth`<span style="font-size: 24px">.</span>

**<span style="font-size: 24px">The problem:</span>**<span style="font-size: 24px"> </span>`data.txt`<span style="font-size: 24px"> contains a massive amount of text — too much to read manually.</span>

**<span style="font-size: 24px">What I did:</span>**

1. `ls`<span style="font-size: 24px"> — found </span>`data.txt`<span style="font-size: 24px"> in the directory</span>

2. `cat data.txt`<span style="font-size: 24px"> — tried reading it, but it was huge</span>

3. <span style="font-size: 24px">Used </span>`grep`<span style="font-size: 24px"> to filter for the specific word:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
cat data.txt | grep "millionth"
```

1. <span style="font-size: 24px">The output showed the line containing </span>`millionth`<span style="font-size: 24px"> and the password right next to it.</span>

**<span style="font-size: 24px">Password for Level 8:</span>**<span style="font-size: 24px"> </span>`VR1ljMayciFxbnUokuQmJFw6QC9VKtub`

---

## <span style="font-size: 24px">The lesson: Pipes (</span>`|`<span style="font-size: 24px">) and </span>`grep`

### <span style="font-size: 24px">The pipe </span>`|`

<span style="font-size: 24px">The pipe takes the output of one command and feeds it into the next command.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
command1 | command2
```

<span style="font-size: 24px">Think of it like a physical pipe carrying water. </span>`command1`<span style="font-size: 24px"> produces output, and that output flows through the pipe into </span>`command2`<span style="font-size: 24px">.</span>

### `grep`

`grep`<span style="font-size: 24px"> searches for a specific word or pattern in text and shows only the matching lines.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
grep "millionth"
```

<span style="font-size: 24px">This means: </span>*<span style="font-size: 24px">"Show me only the lines that contain the word 'millionth'."</span>*

### <span style="font-size: 24px">Together</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
cat data.txt | grep "millionth"
```

<span style="font-size: 24px">Translation:</span>

- `cat data.txt`<span style="font-size: 24px"> → print the whole file</span>

- `|`<span style="font-size: 24px"> → feed that output into the next command</span>

- `grep "millionth"`<span style="font-size: 24px"> → show only lines containing "millionth"</span>

<span style="font-size: 24px">Result: One line from a massive file, containing exactly what you need.</span>

---

## <span style="font-size: 24px">Shortcut (same result, simpler)</span>

<span style="font-size: 24px">You can also just do:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
grep "millionth" data.txt
```

`grep`<span style="font-size: 24px"> can read files directly without needing </span>`cat`<span style="font-size: 24px">. Both work — but the pipe version is useful when you need to chain more commands together.</span>

---

**<span style="font-size: 24px">New tools in your arsenal:</span>**

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">|</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Pipe output from one command to another</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">grep "word"</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Show only lines containing "word"</span></p></td></tr></tbody>
</table>