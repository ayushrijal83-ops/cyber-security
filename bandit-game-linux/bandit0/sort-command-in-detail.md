## `sort`<span style="font-size: 18px"> Command — Full Breakdown</span>

### <span style="font-size: 18px">What it does</span>

`sort`<span style="font-size: 18px"> takes lines of text and arranges them in order — alphabetically by default, or numerically if you tell it to.</span>

<span style="font-size: 18px">It doesn't change the original file. It just outputs the sorted result to your screen.</span>

---

### <span style="font-size: 18px">Basic syntax</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort [options] [filename]
```

<span style="font-size: 18px">If you don't give a filename, </span>`sort`<span style="font-size: 18px"> reads from standard input (like a pipe).</span>

---

### <span style="font-size: 18px">Example 1: Basic sorting</span>

<span style="font-size: 18px">File </span>`fruits.txt`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
banana
apple
cherry
apple
banana
```

<span style="font-size: 18px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort fruits.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
apple
apple
banana
banana
cherry
```

<span style="font-size: 18px">Simple — it sorted everything alphabetically.</span>

---

### <span style="font-size: 18px">Example 2: Sorting numbers (the tricky part)</span>

<span style="font-size: 18px">File </span>`numbers.txt`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
10
2
1
20
3
```

<span style="font-size: 18px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort numbers.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
1
10
2
20
3
```

**<span style="font-size: 18px">Wait — that's wrong!</span>**<span style="font-size: 18px"> Why is </span>`10`<span style="font-size: 18px"> before </span>`2`<span style="font-size: 18px">?</span>

<span style="font-size: 18px">Because by default, </span>`sort`<span style="font-size: 18px"> treats everything as </span>**<span style="font-size: 18px">text</span>**<span style="font-size: 18px">, not numbers. In text order, </span>`"10"`<span style="font-size: 18px"> comes before </span>`"2"`<span style="font-size: 18px"> because </span>`"1"`<span style="font-size: 18px"> comes before </span>`"2"`<span style="font-size: 18px"> alphabetically.</span>

---

### <span style="font-size: 18px">Example 3: Proper numeric sorting with </span>`-n`

<span style="font-size: 18px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort -n numbers.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
1
2
3
10
20
```

<span style="font-size: 18px">Now it's correct. The </span>`-n`<span style="font-size: 18px"> flag tells </span>`sort`<span style="font-size: 18px"> to treat values as numbers.</span>

---

## <span style="font-size: 18px">Important Flags</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Flag</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">What it does</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Example</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-n</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Sort numerically (not as text)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -n file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-r</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Reverse the order</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -r file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-u</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Remove duplicates (like </span><code class="hljs" spellcheck="false">uniq</code><span style="font-size: 18px">)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -u file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-o</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Write output to a file</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt -o sorted.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-t</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Specify a delimiter (for CSV/data files)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -t ',' -k 2 file.csv</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-k</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Sort by a specific column</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -k 2 file.txt</code></p></td></tr></tbody>
</table>

---

### <span style="font-size: 18px">Example 4: Reverse sorting with </span>`-r`

<span style="font-size: 18px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort -r fruits.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
cherry
banana
banana
apple
apple
```

<span style="font-size: 18px">Alphabetical, but reversed (Z to A).</span>

---

### <span style="font-size: 18px">Example 5: Sort + remove duplicates with </span>`-u`

<span style="font-size: 18px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort -u fruits.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
apple
banana
cherry
```

<span style="font-size: 18px">Sorted AND duplicates removed. This does what </span>`sort | uniq`<span style="font-size: 18px"> does, but in one step.</span>

---

### <span style="font-size: 18px">Example 6: Sorting by column with </span>`-k`

<span style="font-size: 18px">File </span>`people.txt`<span style="font-size: 18px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
Alice 30
Bob 25
Charlie 35
David 20
```

<span style="font-size: 18px">To sort by age (the second column):</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort -k 2 -n people.txt
```

<span style="font-size: 18px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
David 20
Bob 25
Alice 30
Charlie 35
```

<span style="font-size: 18px">The </span>`-k 2`<span style="font-size: 18px"> means "sort by column 2" and </span>`-n`<span style="font-size: 18px"> means "treat it numerically."</span>

---

## <span style="font-size: 18px">Why </span>`sort`<span style="font-size: 18px"> matters in Level 8</span>

<span style="font-size: 18px">In Bandit Level 8, the file had thousands of lines, many duplicated. You needed to group identical lines together so </span>`uniq`<span style="font-size: 18px"> could count them.</span>

`uniq`<span style="font-size: 18px"> only works on </span>**<span style="font-size: 18px">adjacent</span>**<span style="font-size: 18px"> duplicate lines. If duplicates are scattered randomly, </span>`uniq`<span style="font-size: 18px"> misses them. That's why </span>`sort`<span style="font-size: 18px"> always comes first:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
sort data.txt | uniq -c
```

`sorted`<span style="font-size: 18px"> groups them → </span>`uniq`<span style="font-size: 18px"> counts them.</span>

---

## <span style="font-size: 18px">Quick Reference</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Result</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Alphabetical order</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -n file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Numerical order</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -r file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Reverse alphabetical</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -u file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Sorted, no duplicates</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort -k 2 file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Sort by column 2</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 18px">The golden rule</span>

> `sort`<span style="font-size: 18px"> before </span>`uniq`<span style="font-size: 18px">. Always. If the data isn't sorted, </span>`uniq`<span style="font-size: 18px"> gives wrong counts.</span>