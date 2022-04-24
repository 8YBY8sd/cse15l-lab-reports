# Lab Report 2 Week 4

Three code changes that my group worked on in lab 3 in order to fix a bug.

> Code Change 1

![image](https://8yby8sd.github.io/cse15l-lab-reports/test1codechange.png)
[test file 1](https://8yby8sd.github.io/markdown-parser/part3.md)

```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.util.Arrays.copyOfRange(Arrays.java:3822)
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:19)
        at MarkdownParse.main(MarkdownParse.java:30)
```

Relationship between the bug, the
symptom, and the failure-inducing input: The MarkDown.java code doesn't check the empty line, so it causes the infinite in the while loop. Hence, it gives error in the output.


> Code Change 2

![image](https://8yby8sd.github.io/cse15l-lab-reports/test2codechange.png)
[test file 2](https://8yby8sd.github.io/markdown-parser/lab3part5t3.md)

```
Exception in thread "main" java.lang.StringIndexOutOfBoundsException: begin 36, end -1, length 43
        at java.base/java.lang.String.checkBoundsBeginEnd(String.java:4601)
        at java.base/java.lang.String.substring(String.java:2704)
        at MarkdownParse.getLinks(MarkdownParse.java:24)
        at MarkdownParse.main(MarkdownParse.java:35)
```

Relationship between the bug, the symptom, and the failure-inducing input: This test file is missing the closeParen for second link. The computer try to find the closeParen for second link, so it runs infinite while loop. Hence, I should add one line code to check the whether there has closeParen in the end of link.


>Code Change 3

![image](https://8yby8sd.github.io/cse15l-lab-reports/test3codechange.png)
[test file 3](https://8yby8sd.github.io/markdown-parser/lab3part5t4.md)

```
Exception in thread "main" java.lang.OutOfMemoryError: Java heap space
        at java.base/java.lang.StringLatin1.newString(StringLatin1.java:769)
        at java.base/java.lang.String.substring(String.java:2709)
        at MarkdownParse.getLinks(MarkdownParse.java:24)
        at MarkdownParse.main(MarkdownParse.java:35)
```

Relationship between the bug, the symptom, and the failure-inducing input: In the lab3part5t4.md, the third link is missing the openParen, closeParen, and website after closeBracket. Because MarkdownParse.java can not find the "(" and ")", so it output error. By fixing that bug, I can add a code to check "(". 