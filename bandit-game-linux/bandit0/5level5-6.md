## <span style="font-size: 18px">Bandit Level 5 → 6</span>

**<span style="font-size: 18px">The challenge:</span>**<span style="font-size: 18px"> The password is stored somewhere under the </span>`inhere`<span style="font-size: 18px"> directory. The target file is:</span>

- <span style="font-size: 18px">human-readable</span>

- <span style="font-size: 18px">1033 bytes in size</span>

- <span style="font-size: 18px">not executable</span>

**<span style="font-size: 18px">The trap:</span>**<span style="font-size: 18px"> Multiple files matched the size and readability criteria. One file was 1033 bytes and readable, but contained a giant block of random garbage — not the password. </span>`find`<span style="font-size: 18px"> narrows the search, but you still need to verify </span>*<span style="font-size: 18px">what</span>*<span style="font-size: 18px"> a file actually is.</span>

**<span style="font-size: 18px">What I did:</span>**

1. `cd inhere`<span style="font-size: 18px"> — moved into the target directory</span>

2. <span style="font-size: 18px">Ran:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find . -type f -readable -size 1033c ! -executable
```

1. <span style="font-size: 18px">Got multiple results</span>

2. <span style="font-size: 18px">Checked each file's type:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find . -type f -readable -size 1033c ! -executable -exec file {} \;
```

1. <span style="font-size: 18px">Found the one that said </span>**<span style="font-size: 18px">ASCII text</span>**<span style="font-size: 18px"> — the rest were </span>`data`

2. `cat`<span style="font-size: 18px"> that file → got the password</span>

**<span style="font-size: 18px">Password for Level 6:</span>**<span style="font-size: 18px"> </span>`pXa26xhMWaC2SvDotA4r9EgZkulOeSBW`

---

## <span style="font-size: 18px">The lesson: </span>`find`<span style="font-size: 18px"> syntax</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find [where] [conditions]
```

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Flag</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">.</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Search current directory (and everything inside it)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-type f</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Only regular files (not folders)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-size 1033c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Exactly 1033 bytes (</span><code class="hljs" spellcheck="false">c</code><span style="font-size: 18px"> = bytes)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-readable</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Files you can read</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">! -executable</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">NOT executable (</span><code class="hljs" spellcheck="false">!</code><span style="font-size: 18px"> = not)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-exec file {} \;</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Run </span><code class="hljs" spellcheck="false">file</code><span style="font-size: 18px"> on every result</span></p></td></tr></tbody>
</table>

**<span style="font-size: 18px">The bigger lesson:</span>**<span style="font-size: 18px"> </span>`find`<span style="font-size: 18px"> is the first step, not the last. Narrow down with conditions, then verify with </span>`file`<span style="font-size: 18px">. Not every readable file is </span>*<span style="font-size: 18px">useful</span>*<span style="font-size: 18px">.</span>