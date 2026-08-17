## `uniq`<span style="font-size: 24px"> Command — Full Breakdown</span>

### <span style="font-size: 24px">What it does</span>

`uniq`<span style="font-size: 24px"> works with </span>**<span style="font-size: 24px">repeated lines</span>**<span style="font-size: 24px">. It either:</span>

- <span style="font-size: 24px">Removes duplicate lines</span>

- <span style="font-size: 24px">Counts how many times each line appears</span>

<span style="font-size: 24px">But there's one </span>**<span style="font-size: 24px">critical rule</span>**<span style="font-size: 24px"> you must never forget:</span>

> `uniq`<span style="font-size: 24px"> only detects duplicates that are next to each other (adjacent).</span>

<span style="font-size: 24px">If identical lines are scattered randomly through a file, </span>`uniq`<span style="font-size: 24px"> will treat them as different lines. That's why </span>`sort`<span style="font-size: 24px"> always comes before </span>`uniq`<span style="font-size: 24px"> — sorting groups the identical lines together first.</span>

---

### <span style="font-size: 24px">Basic syntax</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
uniq [options] [filename]
```

<span style="font-size: 24px">If no filename is given, it reads from standard input (like a pipe).</span>

---

## <span style="font-size: 24px">Example 1: </span>`uniq`<span style="font-size: 24px"> without sorting (the trap)</span>

<span style="font-size: 24px">File </span>`colors.txt`<span style="font-size: 24px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
red
blue
red
red
green
blue
```

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
uniq colors.txt
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
red
blue
red
green
blue
```

**<span style="font-size: 24px">Wait — duplicates still there?</span>**<span style="font-size: 24px"> Yes. Because the duplicates are not adjacent. The two </span>`red`<span style="font-size: 24px"> lines have </span>`blue`<span style="font-size: 24px"> between them. The two </span>`blue`<span style="font-size: 24px"> lines have </span>`red`<span style="font-size: 24px"> and </span>`green`<span style="font-size: 24px"> between them.</span>

`uniq`<span style="font-size: 24px"> only removes duplicates that are </span>**<span style="font-size: 24px">right next to each other</span>**<span style="font-size: 24px">.</span>

---

## <span style="font-size: 24px">Example 2: </span>`uniq`<span style="font-size: 24px"> after sorting (correct usage)</span>

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort colors.txt | uniq
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
blue
green
red
```

<span style="font-size: 24px">Now all identical lines were grouped by </span>`sort`<span style="font-size: 24px">, so </span>`uniq`<span style="font-size: 24px"> could remove them properly.</span>

---

## <span style="font-size: 24px">Example 3: </span>`uniq -c`<span style="font-size: 24px"> — count duplicates</span>

<span style="font-size: 24px">The </span>`-c`<span style="font-size: 24px"> flag adds a count to each line, showing how many times it appeared.</span>

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort colors.txt | uniq -c
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
2 blue
1 green
2 red
```

<span style="font-size: 24px">Now you see:</span>

- `blue`<span style="font-size: 24px"> appears 2 times</span>

- `green`<span style="font-size: 24px"> appears 1 time</span>

- `red`<span style="font-size: 24px"> appears 2 times</span>

<span style="font-size: 24px">This is exactly what you used in Bandit Level 8.</span>

---

## <span style="font-size: 24px">Important Flags</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Flag</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">What it does</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Example</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Count occurrences of each line</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -c file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-d</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Show only lines that are duplicated (appear more than once)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -d file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-u</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Show only lines that are unique (appear exactly once)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -u file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-i</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Ignore case (treat "Red" and "red" as same)</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -i file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-f N</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Skip first N fields (columns) when comparing</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -f 1 file.txt</code></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">-s N</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Skip first N characters when comparing</span></p></td><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -s 5 file.txt</code></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">Example 4: </span>`uniq -d`<span style="font-size: 24px"> — show only duplicates</span>

<span style="font-size: 24px">File </span>`names.txt`<span style="font-size: 24px"> (already sorted):</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
alice
alice
bob
charlie
charlie
charlie
david
```

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
uniq -d names.txt
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
alice
charlie
```

<span style="font-size: 24px">Only the lines that appear more than once.</span>

---

## <span style="font-size: 24px">Example 5: </span>`uniq -u`<span style="font-size: 24px"> — show only unique lines</span>

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
uniq -u names.txt
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
bob
david
```

<span style="font-size: 24px">Only the lines that appear exactly once. This is actually a shortcut for what you did in Bandit Level 8 — you could have used </span>`sort | uniq -u`<span style="font-size: 24px"> instead of </span>`sort | uniq -c | grep "1 "`<span style="font-size: 24px">.</span>

---

## <span style="font-size: 24px">Example 6: </span>`uniq -i`<span style="font-size: 24px"> — ignore case</span>

<span style="font-size: 24px">File </span>`mixed.txt`<span style="font-size: 24px">:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
Apple
apple
APPLE
banana
Banana
```

<span style="font-size: 24px">Command:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort mixed.txt | uniq -i
```

<span style="font-size: 24px">Output:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
Apple
banana
```

<span style="font-size: 24px">It treats </span>`Apple`<span style="font-size: 24px">, </span>`apple`<span style="font-size: 24px">, and </span>`APPLE`<span style="font-size: 24px"> as the same thing.</span>

---

## <span style="font-size: 24px">The Golden Rule (repeated on purpose)</span>

> `sort`<span style="font-size: 24px"> before </span>`uniq`<span style="font-size: 24px">. Always.</span>

<span style="font-size: 24px">Pipeline pattern:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort file.txt | uniq -c
```

<span style="font-size: 24px">This is one of the most common command patterns in all of Linux. You'll use it constantly — in Bandit, in CTFs, in log analysis, in real pentests.</span>

---

## <span style="font-size: 24px">Quick Reference</span>

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 24px">Result</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Remove adjacent duplicates</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt | uniq</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Remove ALL duplicates</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt | uniq -c</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Count occurrences of each line</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt | uniq -d</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Show only duplicated lines</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">sort file.txt | uniq -u</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Show only unique lines</span></p></td></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">uniq -i file.txt</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 24px">Ignore case differences</span></p></td></tr></tbody>
</table>

---

## <span style="font-size: 24px">How this connects to Bandit Level 8</span>

<span style="font-size: 24px">You needed the line that appeared exactly once. The chain was:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort data.txt | uniq -c | grep "1 "
```

<span style="font-size: 24px">But now you know a cleaner way:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 24px">text</span>

```
sort data.txt | uniq -u
```

<span style="font-size: 24px">Same result, fewer commands. That's what mastery looks like — knowing multiple ways to solve the same problem and picking the cleanest one.</span>