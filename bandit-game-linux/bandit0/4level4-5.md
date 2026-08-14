## <span style="font-size: 18px">Bandit Level 4 → 5</span>

**<span style="font-size: 18px">The challenge:</span>**<span style="font-size: 18px"> The password is stored in the only human-readable file in the </span>`inhere`<span style="font-size: 18px"> directory.</span>

**<span style="font-size: 18px">What I did:</span>**

1. `cd inhere`<span style="font-size: 18px"> — moved into the target directory</span>

2. `ls -la`<span style="font-size: 18px"> — listed all files, found 10 files named </span>`-file00`<span style="font-size: 18px"> through </span>`-file09`

3. `file ./*`<span style="font-size: 18px"> — checked what type of data was inside each file</span>

4. <span style="font-size: 18px">Found that </span>`-file07`<span style="font-size: 18px"> was </span>**<span style="font-size: 18px">ASCII text</span>**<span style="font-size: 18px"> — the only human-readable file</span>

5. `cat ./-file07`<span style="font-size: 18px"> — read the file, got the password</span>

**<span style="font-size: 18px">Password for Level 5:</span>**<span style="font-size: 18px"> </span>`6C7h9GD8M6ai5nr7wo1RonrzFjj9yIrG`

---

**<span style="font-size: 18px">The lesson:</span>**

- `ls -la`<span style="font-size: 18px"> shows filenames, but </span>**<span style="font-size: 18px">not</span>**<span style="font-size: 18px"> what's inside them.</span>

- `file`<span style="font-size: 18px"> reveals the actual content type (ASCII text, binary, data, etc.).</span>

- <span style="font-size: 18px">Always check the file type before wasting time reading everything.</span>

- <span style="font-size: 18px">Filenames starting with </span>`-`<span style="font-size: 18px"> need </span>`./`<span style="font-size: 18px"> in front (learned this in Level 1).</span>

---

**<span style="font-size: 18px">New command learned:</span>**

<table>
<tbody><tr><th colspan="1" rowspan="1"><p><span style="font-size: 18px">Command</span></p></th><th colspan="1" rowspan="1"><p><span style="font-size: 18px">What it does</span></p></th></tr><tr><td colspan="1" rowspan="1"><p><code class="hljs" spellcheck="false">file ./*</code></p></td><td colspan="1" rowspan="1"><p><span style="font-size: 18px">Shows the type of every file in the current directory</span></p></td></tr></tbody>
</table>

---

<span style="font-size: 18px">Ready for Level 5 → 6. This one is all about the </span>`find`<span style="font-size: 18px"> command.</span>