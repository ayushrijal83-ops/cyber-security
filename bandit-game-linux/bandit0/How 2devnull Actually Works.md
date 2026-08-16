## <span style="font-size: 18px">How </span>`2>/dev/null`<span style="font-size: 18px"> Actually Works</span>

### <span style="font-size: 18px">Step 1: Linux has 3 standard "streams"</span>

<span style="font-size: 18px">Every command you run produces output, but not all output is the same. Linux separates them into three channels:</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Stream</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Number</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Purpose</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><strong><span style="font-size: 18px">stdin</span></strong></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">0</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Input (what you type)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong><span style="font-size: 18px">stdout</span></strong></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">1</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Normal output (successful results)</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><strong><span style="font-size: 18px">stderr</span></strong></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">2</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Error output (warnings, failures)</span></p></td></tr></tbody>
</table>

---

### <span style="font-size: 18px">Step 2: What </span>`>`<span style="font-size: 18px"> does</span>

`>`<span style="font-size: 18px"> is </span>**<span style="font-size: 18px">redirection</span>**<span style="font-size: 18px">. It takes output from one stream and sends it somewhere else.</span>

<span style="font-size: 18px">Example:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / > results.txt
```

<span style="font-size: 18px">This sends </span>`stdout`<span style="font-size: 18px"> (stream 1) to a file called </span>`results.txt`<span style="font-size: 18px">.</span>

<span style="font-size: 18px">But by default, </span>`>`<span style="font-size: 18px"> only redirects </span>**<span style="font-size: 18px">stdout</span>**<span style="font-size: 18px"> — the normal output. Errors still appear on your screen.</span>

---

### <span style="font-size: 18px">Step 3: What </span>`2>`<span style="font-size: 18px"> does</span>

`2>`<span style="font-size: 18px"> specifically redirects </span>**<span style="font-size: 18px">stderr</span>**<span style="font-size: 18px"> (stream 2) — the error messages.</span>

<span style="font-size: 18px">Example:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / 2> errors.txt
```

<span style="font-size: 18px">This sends all the </span>`Permission denied`<span style="font-size: 18px"> messages to </span>`errors.txt`<span style="font-size: 18px">, while the useful results still print on screen.</span>

---

### <span style="font-size: 18px">Step 4: What </span>`/dev/null`<span style="font-size: 18px"> is</span>

`/dev/null`<span style="font-size: 18px"> is a special file in Linux. It's a </span>**<span style="font-size: 18px">black hole</span>**<span style="font-size: 18px"> — anything sent there disappears forever.</span>

<span style="font-size: 18px">It's not a real file. It's a virtual device that discards everything written to it.</span>

---

### <span style="font-size: 18px">Step 5: Put it together</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

<span style="font-size: 18px">Translation:</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Part</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Meaning</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">find / ...</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Run the find command</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">2&gt;</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Take the error stream</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">/dev/null</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">And throw it into the black hole</span></p></td></tr></tbody>
</table>

<span style="font-size: 18px">Result: </span>**<span style="font-size: 18px">Errors disappear. Only useful output remains.</span>**

---

## <span style="font-size: 18px">Real-world example</span>

<span style="font-size: 18px">Without </span>`2>/dev/null`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
$ find / -name "*.conf"
/etc/resolv.conf
find: '/root': Permission denied
find: '/proc/1/map_files': Permission denied
/etc/host.conf
find: '/var/lib/private': Permission denied
```

<span style="font-size: 18px">With </span>`2>/dev/null`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
$ find / -name "*.conf" 2>/dev/null
/etc/resolv.conf
/etc/host.conf
```

<span style="font-size: 18px">Clean. Only the good stuff.</span>

---

## <span style="font-size: 18px">Bonus: What about </span>`1>`<span style="font-size: 18px">?</span>

`1>`<span style="font-size: 18px"> redirects </span>**<span style="font-size: 18px">stdout</span>**<span style="font-size: 18px"> (normal output). It's the default, so </span>`>`<span style="font-size: 18px"> and </span>`1>`<span style="font-size: 18px"> are the same thing.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
find / > results.txt        # stdout to file
find / 1> results.txt       # same thing
find / 2> errors.txt        # stderr to file
find / > all.txt 2>&1       # both streams to same file
```

<span style="font-size: 18px">The last one (</span>`2>&1`<span style="font-size: 18px">) means "send stderr wherever stdout is going."</span>

---

## <span style="font-size: 18px">Short version</span>

- `2>`<span style="font-size: 18px"> = "take the error messages"</span>

- `/dev/null`<span style="font-size: 18px"> = "throw them in the trash"</span>

- <span style="font-size: 18px">Together = "shut up about errors, show me only what matters"</span>