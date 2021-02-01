## Markdown

[markdownguide.org](https://www.markdownguide.org/) is very useful for markdown notes.

Here are some of my notes on how to use Markdown:

[Text Formatting](#text-formatting)  
[Lists](#lists)

### Text Formatting

* _italics_: use `_underscores_`
* **bold**: use `**two asterixes**`
* ***bold and italic***: use `***three asterixes***`
* ~~strikethrough~~: `~~two tildas~~`
* code: `` `backticks` ``
* [links](): `[text](url)`
* line break: use two spaces

#### Blockquotes

`> use a carrot in front of your paragaraph to make a block quote`
> this is what a block quote looks like

````
```
use three backticks for a code block
```
````

### Lists
To do unordered lists, use one asterix or dash:
```
* Something
* Something Else

- A Thing
- Another thing
```
- A Thing
- Another thing


And for ordered lists, use numbers:
```
1. The first item
2. The second item
3. The third item
```
1. The first item
2. The second item
3. The third item


Nest lists using spaces:
```
1. The first item
 2. The second item
  3. The third item
```
1. The first item
   1. The second item
      - The third item

# Tables
Use columns and pipes. dashes and colons can be used to make text left `:--`, right `--:`, or center `-:-`.

```
| Header 1       | Header 2       | Header 3     |
| :------------- | :------------: | -----------: |
| left           | right          | center       |
| foo            | bar            | baz          |
```

| Header 1       | Header 2       | Header 3     |
| :------------- | :------------: | -----------: |
| left           | right          | center       |
| foo            | bar            | baz          |

:joy:

Here's a simple footnote,[^1] and here's a longer one.[^bignote]

[^1]: This is the first footnote.

[^bignote]: Here's one with multiple paragraphs and code.

    Indent paragraphs to include them in the footnote.

    `{ my code }`

    Add as many paragraphs as you like.