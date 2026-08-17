## <span style="font-size: 24px">Bandit Level 8 → 9</span>

**<span style="font-size: 24px">The challenge:</span>**<span style="font-size: 24px"> The password is the only line in </span>`data.txt`<span style="font-size: 24px"> that occurs exactly once.</span>

**<span style="font-size: 24px">What I did:</span>**

1. `ls`<span style="font-size: 24px"> — found </span>`data.txt`

2. <span style="font-size: 24px">Tried </span>`cat data.txt`<span style="font-size: 24px"> — too many lines to read manually</span>

3. <span style="font-size: 24px">Used a chain of commands to sort, count, and filter:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort data.txt | uniq -c | grep "1 "
```

**<span style="font-size: 24px">Password for Level 9:</span>**<span style="font-size: 24px"> </span>`EjmOSvuAu7sGAHqHVcBDPirRe9T03kxl`

---

## <span style="font-size: 24px">New commands learned</span>

### `sort`

<span style="font-size: 24px">Sorts lines alphabetically so identical lines are next to each other.</span>

<span style="font-size: 24px">Before:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
banana
apple
banana
cherry
```

<span style="font-size: 24px">After </span>`sort`<span style="font-size: 24px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
apple
banana
banana
cherry
```

### `uniq -c`

<span style="font-size: 24px">Counts how many times each line appears </span>**<span style="font-size: 24px">after sorting</span>**<span style="font-size: 24px">.</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
2 banana
1 apple
1 cherry
```

### <span style="font-size: 24px">The full chain</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort data.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Groups identical lines together</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">| uniq -c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Counts occurrences of each line</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">| grep "1 "</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Shows only the line that appears once</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">The lesson</span>

<span style="font-size: 24px">You rarely solve problems with one command alone. Pipes let you </span>**<span style="font-size: 24px">chain simple tools into powerful pipelines</span>**<span style="font-size: 24px">. </span>`sort`<span style="font-size: 24px"> → </span>`uniq`<span style="font-size: 24px"> → </span>`grep`<span style="font-size: 24px"> is a classic pattern you'll use again and again.</span>