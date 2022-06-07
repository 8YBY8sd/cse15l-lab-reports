# Lab Report 4 Week 8

> How you found the tests with different results 

I used vimdiff on the results of running a bash for loop found the tests with different results.
`vimdiff` takes two files as arguments and shows their differences side by side.
We can put this `$ vimdiff my-markdown-parser/results.txt cse15lsp22-markdown-parser/results.txt` in the command line, and then it gave us some differences shown in the following screenshot:

![result](https://8yby8sd.github.io/cse15l-lab-reports/result.png)

---

> Two tests from the 652 tests where your implementation (or a representative implementation from your group) had different answers than the implementation we provided for lab 9.

### Test 1
[test-file 139](https://github.com/nidhidhamnani/markdown-parser/blob/main/test-files/139.md) gets different results.


my-markdown-parser implementation is wrong, and cse15lsp22-markdown-parser implementation is correct.  
![139](https://8yby8sd.github.io/cse15l-lab-reports/labreport5139.png)

Here is VScode preview of the 139.md.
![labreport5139preview](https://8yby8sd.github.io/cse15l-lab-reports/labreport5139preview.png)

The oupt put should be `[]`because there doesn't have any links in this file.

Fix: For my-markdown-parser, it doesn't return `[]` when it can't find any `[ ] ( )` in the test file.


### Test 2