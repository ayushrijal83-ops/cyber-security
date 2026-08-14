## <span style="font-size: 18px">Bandit Level 3 → 4</span>

**<span style="font-size: 18px">The task:</span>**<span style="font-size: 18px"> Password is stored in a hidden file inside the </span>`inhere`<span style="font-size: 18px"> directory.</span>

**<span style="font-size: 18px">What I did:</span>**

1. `ls`<span style="font-size: 18px"> — listed the current directory, found a folder called </span>`inhere`

2. `cd inhere`<span style="font-size: 18px"> — moved into that folder</span>

3. `ls -la`<span style="font-size: 18px"> — listed </span>**<span style="font-size: 18px">all</span>**<span style="font-size: 18px"> files, including hidden ones</span>

4. <span style="font-size: 18px">Found a hidden file called </span>`...hidden...`

5. `cat`<span style="font-size: 18px"> — read the file, got the password</span>

**<span style="font-size: 18px">Password for Level 4:</span>**<span style="font-size: 18px"> </span>`xzTXq1rDJQVVAzdv5cHq1TQytTWufAMq`

---

## <span style="font-size: 18px">The key lesson: </span>`ls -la`

<span style="font-size: 18px">Let's be precise on what the flags mean, because you'll use this constantly:</span>

- `ls -l`<span style="font-size: 18px"> → long format (permissions, owner, size, date)</span>

- `ls -a`<span style="font-size: 18px"> → show </span>**<span style="font-size: 18px">all</span>**<span style="font-size: 18px"> files, including hidden ones</span>

- `ls -la`<span style="font-size: 18px"> → both together</span>

**<span style="font-size: 18px">What makes a file "hidden"?</span>**

<span style="font-size: 18px">Any file or folder whose name starts with a </span>`.`<span style="font-size: 18px"> (dot) is hidden from normal </span>`ls`<span style="font-size: 18px">. Examples:</span>

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
.hiddenfile
.config
.bashrc
```

<span style="font-size: 18px">Normal </span>`ls`<span style="font-size: 18px"> ignores these. </span>`ls -a`<span style="font-size: 18px"> reveals them.</span>