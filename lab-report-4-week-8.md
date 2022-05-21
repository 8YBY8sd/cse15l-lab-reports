# Lab Report 4 Week 8

Test three markdown snippets

[Link of my markdown-parse repository:](https://github.com/8YBY8sd/markdown-parse)

[Link of the one I reviewed in week 7:](https://github.com/rmccrystal/markdown-parser)

> Snippet 1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

markdown-parse should produce:

```
[a link](url.com)

another link`

cod[e

code]
```

The code in MarkdownParseTest.java for how I turned it into a test:
```
    public void snippet1() throws IOException {
        List<String> list = List.of("[a link](url.com)", "another link`", "cod[e", "code]");
        Path fileName = Path.of("snippet1.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        assertEquals(list, links);
    }
```

Test it in my markdown-parse: failure
![snippet1mytest](https://8yby8sd.github.io/cse15l-lab-reports/snippet1mytest.png)

Test it in the one I reviewed in week 7: failure
![snippet1othertest](https://8yby8sd.github.io/cse15l-lab-reports/snippet1othertest.png)

---

> Snippet 2

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```

markdown-parse should produce

```
[a nested link](b.com)

a nested parenthesized url

some escaped [ brackets ]
```
The code in MarkdownParseTest.java for how I turned it into a test:
```
    @Test
    public void snippet2() throws IOException {
        List<String> list = List.of("[a nested link](b.com)", "a nested parenthesized url", "some escaped [ brackets ]");
        Path fileName = Path.of("snippet2.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        assertEquals(list, links);
    }
```

Test it in my markdown-parse: failure
![snippet2mytest](https://8yby8sd.github.io/cse15l-lab-reports/snippet2mytest.png)

Test it in the one I reviewed in week 7: failure
![snippet2othertest](https://8yby8sd.github.io/cse15l-lab-reports/snippet2othertest.png)

---

> Snippet 3

```
[this title text is really long and takes up more than 
one line

and has some line breaks](
    https://www.twitter.com
)

[this title text is really long and takes up more than 
one line](
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
)


[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/



)

And then there's more text
```

markdown-parse should produce

```
[this title text is really long and takes up more than one line

and has some line breaks]( https://www.twitter.com )

this title text is really long and takes up more than one line

[this link doesn't have a closing parenthesis](github.com

And there's still some more text after that.

[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/

)

And then there's more text
```

The code in MarkdownParseTest.java for how I turned it into a test:
```
    @Test
    public void snippet3() throws IOException {
        List<String> list = List.of("[this title text is really long and takes up more than one line", "and has some line breaks]( https://www.twitter.com )", "this title text is really long and takes up more than one line", "[this link doesn't have a closing parenthesis](github.com", "And there's still some more text after that.", "[this link doesn't have a closing parenthesis for a while](https://cse.ucsd.edu/", ")", "And then there's more text");
        Path fileName = Path.of("snippet3.md");
        String content = Files.readString(fileName);
        ArrayList<String> links = MarkdownParse.getLinks(content);
        assertEquals(list, links);
    }
```

Test it in my markdown-parse: failure
![snippet3mytest](https://8yby8sd.github.io/cse15l-lab-reports/snippet3mytest.png)

Test it in the one I reviewed in week 7: failure
![snippet3othertest](https://8yby8sd.github.io/cse15l-lab-reports/snippet3othertest.png)