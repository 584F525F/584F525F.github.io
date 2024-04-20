<!-- https://www.youtube.com/watch?v=NY7DHvo1XVM&t=2349s -->
# Subject Title

> Subject description - reference

[icons](https://emojipedia.org/emoji-1.0)
🏴‍☠️
🥽 
🧪
🔬
🐍
🦕
🐲
🛸
👽
👾
🖥️
🛠️
🚧
🧰
🧯
🕹️
🎮
📺
📼
💾

---
## Images
[Images Reference](https://squidfunk.github.io/mkdocs-material/reference/images/)

![Image title](https://dummyimage.com/600x400/eee/aaa){ align=center }

![Image title](../docs/assets/images/comingsoon.gif){ align=center }

#OR

<figure markdown="span">
  ![Image title](https://dummyimage.com/600x400/){ width="300" }
  <figcaption>Image caption</figcaption>
</figure>
---

## links in new tab

[my-link]{:target="_blank"} within a sentence and  [my-link]: http://google.com for referencing. (Note that there are two leading spaces).
---

## code

Summary `code code code` something stuff

```py hl_lines="1" title="py"
do stuff
print something
```

---

### Task Lists

- [x] #739
- [ ] https://github.com/740
- [ ] Add delight to the experience when all tasks are complete :tada:

---

## blocks

### non Collapsible blocks
!!! example
	BODY HERE

### Collapsible blocks
??? note "title"
    BODY HERE
	
### expanded block by default
???+ note
	BODY HERE

??? note "note"
    note

??? abstract "abstract"
    abstract

??? info "info"
    info

??? tip "tip"
    tip

??? success "success"
    success

??? question "question"
    question

??? warning "warning"
    warning

??? failure "failure"
    failure

??? danger "danger"
    danger

??? bug "bug"
    bug

??? example "example"
    example

??? quote "quote"
    quote



### collapsed section

<details>

<summary>Title</summary>

##### header
summary
```py hl_lines="1" title="py"
   print Hello World
```

</details>

---

## grouping tabs & code blocks

### code
=== "C"

    ``` c
	  {
		code here
    }
    ```

=== "C++"

    ``` c++
	{
		code here
    }
    ```

### grouping tabs in a block

!!! example "title"
=== "Unordered list"

    * e
    * f

=== "Ordered list"

    1. a
    2. b

---

## References
- [Blog title - Author, Date](https://example.com)

---

## Image size & path

![](/Knowledge_Base/images/image-2.png){: style="height:150px;width:150px"}

/Knowledge_Base/images/

## To embed a PDF file simple use the following syntax.

(pypi.org mkdocs-pdf)[https://pypi.org/project/mkdocs-pdf/]

![Alt text](<path to pdf>){ type=application/pdf }
Optionally, you can specify style constraints, e.g.

![Alt text](<path to pdf>){ type=application/pdf style="min-height:25vh;width:100%" }


<!--- file: docs/howto/embedding_pdf.md --->
{% with pdf_file = "/Knowledge_Base/images/javvin-tcpipguide-pdf.pdf" %}

{% set solid_filepdf = '<i class="fas fa-file-pdf"></i>' %}
{% set empty_filepdf = '<i class="far fa-file-pdf"></i>' %}

## Example: Embedding a PDF file

<object data="{{ pdf_file }}" type="application/pdf">
    <embed src="{{ pdf_file }}" type="application/pdf" />
</object>

## Example: Creating a link to a PDF file

<a href="{{ pdf_file }}" class="image fit">{{ solid_filepdf }}</a>

{% endwith %}

