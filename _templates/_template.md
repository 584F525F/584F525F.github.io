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

---

## PDFs

[click to open PDF in new tab](/Knowledge_Base/images/javvin-tcpipguide-pdf.pdf)

<embed src="/Knowledge_Base/images/javvin-tcpipguide-pdf.pdf" type="application/pdf" style="min-height:100vh;width:100%">


[click to open PDF in new tab](XXXXXXXX)

<embed src="XXXXXXXX" type="application/pdf" style="min-height:100vh;width:100%">

---

## Tables

| Method      | Description                          |
| ----------- | ------------------------------------ |
| `GET`       | :material-check:     Fetch resource  |
| `PUT`       | :material-check-all: Update resource |
| `DELETE`    | :material-close:     Delete resource |

---




<mark>Color Mark Yellow</mark>

