## <span style="font-size: 24px">Bandit Level 9 → 10</span>

**<span style="font-size: 24px">The challenge:</span>**<span style="font-size: 24px"> The password is stored in </span>`data.txt`<span style="font-size: 24px"> as one of the few human-readable strings, preceded by several </span>`=`<span style="font-size: 24px"> characters.</span>

**<span style="font-size: 24px">What I did:</span>**

1. `ls`<span style="font-size: 24px"> — found </span>`data.txt`

2. `cat data.txt`<span style="font-size: 24px"> — saw garbage (binary data, not plain text)</span>

3. <span style="font-size: 24px">Used </span>`strings`<span style="font-size: 24px"> to extract only the readable text, then filtered with </span>`grep`<span style="font-size: 24px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
strings data.txt | grep "===="
```

1. <span style="font-size: 24px">The output showed lines with </span>`====`<span style="font-size: 24px"> and the password right there.</span>

**<span style="font-size: 24px">Password for Level 10:</span>**<span style="font-size: 24px"> </span>*<span style="font-size: 24px">(add it here)</span>*

---

## <span style="font-size: 24px">New command learned</span>

### `strings`

<span style="font-size: 24px">Extracts human-readable text from binary files. It ignores all the machine-format garbage and shows only the readable strings.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
strings data.txt
```

### <span style="font-size: 24px">Combined with </span>`grep`

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
strings data.txt | grep "===="
```

- `strings data.txt`<span style="font-size: 24px"> → extract readable text</span>

- `| grep "===="`<span style="font-size: 24px"> → show only lines containing </span>`====`

---

## <span style="font-size: 24px">The lesson</span>

<span style="font-size: 24px">Not every file is plain text. When </span>`cat`<span style="font-size: 24px"> shows garbage, the file is probably binary. </span>`strings`<span style="font-size: 24px"> is your tool for pulling useful information out of it.</span>

---

**<span style="font-size: 24px">Your toolkit so far:</span>**

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">ls</code><span style="font-size: 24px"> / </span><code class="hljs" spellcheck="false">ls -la</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">List files (including hidden)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">cat</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Read files</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">file</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Check file type</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">find</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Search for files</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Sort lines</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Count duplicate lines</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">grep</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Filter for specific text</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">strings</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Extract readable text from binary</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">|</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Pipe output between commands</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">./</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Handle weird filenames</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">\</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Escape special characters</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">2&gt;/dev/null</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Suppress error messages</span></p></td></tr></tbody>
</table>