# Lab Report 2 Week 4

Three code changes that my group worked on in lab 3 in order to fix a bug.

> code change 1


[test file 1](https://8yby8sd.github.io/markdown-parser/part3.html)

```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOfRange(Arrays.java:3822)
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:19)
        at MarkdownParse.main(MarkdownParse.java:29)
```

Relationship between the bug, the
symptom, and the failure-inducing input: The MarkDown.java code doesn't check the empty line, so it causes the infinite in the while loop. Hence, it gives error in the output.


> code change 2

