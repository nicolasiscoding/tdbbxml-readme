# tdbbxml

Oversimplifying the problem and context:
1. We are doing rich text injetion (paragraphs, tables, lists, bold, underline, etc) and our engine requires template files to have an "@" symbol as part of the tag.
For example:

   - `{Name}` is a string whereas
   - `{@List}` would be a rich text list. 
   
For the end user's sake, we only require them to use a normal tag `{List}` instead of `{@List}` for both use cases, and pre-process the files to determine which tags have the ability for rich text injection and which tags do **not** have the ability for rich text injection. 

A tag is eligible for rich text injection if it is the only item within the a paragraph. A paragraph in OOXML is defined as <w:p> (http://officeopenxml.com/WPsection.php)

**Not capable of rich text injection**
```
The cat named {catName} can jumped over the mouse.
```

**Capabable of rich text injection**
```
Dear Susan,

{richTextElement}

Signed,

Nicolas
```

Your task is to iterate through `word/document.xml`, all headers and footers to perform this replacement given a list of tags:

```
Dear Susan,

{@richTextElement}

Signed,

Nicolas
```

