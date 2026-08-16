## <span style="font-size: 18px">Bandit Level 6 → 7</span>

**<span style="font-size: 18px">The challenge:</span>**<span style="font-size: 18px"> The password is stored </span>*<span style="font-size: 18px">somewhere on the entire server</span>*<span style="font-size: 18px"> — not just in the </span>`inhere`<span style="font-size: 18px"> directory. The target file is:</span>

- <span style="font-size: 18px">Owned by user </span>`bandit7`

- <span style="font-size: 18px">Owned by group </span>`bandit6`

- <span style="font-size: 18px">Exactly 33 bytes in size</span>

**<span style="font-size: 18px">What I did:</span>**

1. <span style="font-size: 18px">Searched the whole filesystem from root (</span>`/`<span style="font-size: 18px">):</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / -user bandit7 -group bandit6 -size 33c
```

1. <span style="font-size: 18px">Got flooded with </span>`Permission denied`<span style="font-size: 18px"> errors — normal when searching outside your home directory.</span>

2. <span style="font-size: 18px">Suppressed the errors by redirecting them to </span>`/dev/null`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

1. <span style="font-size: 18px">Got one clean file path back.</span>

2. `cat`<span style="font-size: 18px"> that file → password found.</span>

**<span style="font-size: 18px">Password for Level 7:</span>**<span style="font-size: 18px"> </span>`Bmnnvf82KzQlfxgAI2d1zYbr1u9pr3E3`

---

## <span style="font-size: 18px">New </span>`find`<span style="font-size: 18px"> flags learned</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Flag</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-user [name]</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">File owned by a specific user</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-group [name]</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">File belongs to a specific group</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-size [n]c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">File exactly n bytes</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">/</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Search from the root of the entire filesystem</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">2&gt;/dev/null</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Send all error messages to a black hole (show only clean results)</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 18px">The lesson</span>

`find`<span style="font-size: 18px"> is not just for local folders — you can scan an entire filesystem. When you scan outside your own directory, errors are expected. </span>`2>/dev/null`<span style="font-size: 18px"> keeps the output clean so you only see what matters.</span>