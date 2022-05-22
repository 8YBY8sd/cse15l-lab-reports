# Lab Report 4 Week 8

Test three markdown snippets

[Link of my markdown-parse repository](https://github.com/8YBY8sd/markdown-parse)

[Link of the one I reviewed in week 7](https://github.com/rmccrystal/markdown-parser)

> Snippet 1

```
`[a link`](url.com)

[another link](`google.com)`

[`cod[e`](google.com)

[`code]`](ucsd.edu)
```

![snippet1](https://8yby8sd.github.io/cse15l-lab-reports/snippet1.png)

![snippet1produce](https://8yby8sd.github.io/cse15l-lab-reports/snippet1produce.png)

markdown-parse should produce: 

```
`google.com, google.com, ucsd.edu
```


The code in MarkdownParseTest.java for how I turned it into a test:
```
    public void snippet1() throws IOException {
        List<String> list = List.of("`google.com", "google.com", "ucsd.edu");
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

Small change:

There is a small change (<10 lines>) that will make my program work for snippet 1 and all related cases that use inline code with backticks. we check that if there is have odd numbers of backticks inside of the "[" and "]", it would not print out the link.

---

> Snippet 2

```
[a [nested link](a.com)](b.com)

[a nested parenthesized url](a.com(()))

[some escaped \[ brackets \]](example.com)
```
![snippet2](https://8yby8sd.github.io/cse15l-lab-reports/snippet2.png)

![snippet2produce](https://8yby8sd.github.io/cse15l-lab-reports/snippet2produce.png)

markdown-parse should produce

```
a.com, a.com, example.com
```

The code in MarkdownParseTest.java for how I turned it into a test:
```
    @Test
    public void snippet2() throws IOException {
        List<String> list = List.of("a.com", "a.com", "example.com");
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

Small change:

There is a small (<10 lines) code change that will make my program work for snippet 2 and all related cases that nest parentheses, brackets, and escaped brackets. First, it should print out the link from the "(" and ")" when there is a "(" and ")" after first "[" and "]" if it is valid in snippet 1. Second, if there are even numbers of "[", "]", "(", and ")" inside of "[" and "]", it should not print out the link after this "]" which is inside of "(" and ")".

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
![snippet3](https://8yby8sd.github.io/cse15l-lab-reports/snippet3.png)

![snippet3produce](https://8yby8sd.github.io/cse15l-lab-reports/snippet3produce.png)

markdown-parse should produce

```
https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule
```



The code in MarkdownParseTest.java for how I turned it into a test:
```
    @Test
    public void snippet3() throws IOException {
        List<String> list = List.of("https://sites.google.com/eng.ucsd.edu/cse-15l-spring-2022/schedule");
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

Small change:

There is a small (<10 lines) code change that will make my program work for snippet 3 and all related cases that have newlines in brackets and parentheses. First, it needs to check there doesn't have one empty line after "(" or before ")". Second, it needs to check there doesn't have any space before the link. finally, it needs to check there doesn't have any empty lines between the middle of brackets and parentheses.