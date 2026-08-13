## <span style="font-size: 18px">Bandit Level 2 → 3</span>

**<span style="font-size: 18px">The challenge:</span>**<span style="font-size: 18px"> The filename had spaces in it. Normally, the shell splits commands by spaces, so </span>`cat spaces in this filename`<span style="font-size: 18px"> would be treated as four separate arguments.</span>

**<span style="font-size: 18px">The fix:</span>**<span style="font-size: 18px"> Use </span>`\`<span style="font-size: 18px"> (backslash) before each space to "escape" it — telling the shell </span>*<span style="font-size: 18px">"this space is a character, not a separator."</span>*

**<span style="font-size: 18px">My actual command:</span>**

<span style="font-family: Menlo, Monaco, Consolas, Cascadia Mono, Ubuntu Mono, DejaVu Sans Mono, Liberation Mono, JetBrains Mono, Fira Code, Cousine, Roboto Mono, Courier New, Courier, sans-serif, system-ui; color: rgb(15, 17, 21); font-size: 18px">text</span>

```
cat ./--spaces\ in\ this\ filename--
```

**<span style="font-size: 18px">Why</span>** `./`<span style="font-size: 18px"> at the start? The filename also started with dashes (</span>`--spaces...`<span style="font-size: 18px">). Just like the </span>`-`<span style="font-size: 18px"> file from Level 1, commands might interpret </span>`--`<span style="font-size: 18px"> as a flag. Adding </span>`./`<span style="font-size: 18px"> in front means </span>*<span style="font-size: 18px">"this is a file path in the current directory, not a flag."</span>*

<span style="font-size: 18px">So the full command solves </span>**<span style="font-size: 18px">two problems at once</span>**<span style="font-size: 18px">:</span>

- `./`<span style="font-size: 18px"> → handles the leading dashes</span>

- `\`<span style="font-size: 18px"> → handles the spaces</span>

**<span style="font-size: 18px">Password for Level 3:</span>**<span style="font-size: 18px"> </span>`7ZZ2LFrykP2zEyvBl4m3clcL7tGYJPME`

**<span style="font-size: 18px">The lesson:</span>**<span style="font-size: 18px"> Weird filenames are a common real-world obstacle. </span>`./`<span style="font-size: 18px"> and </span>`\`<span style="font-size: 18px"> are your two tools for handling them. Tab autocomplete also does this automatically.</span>