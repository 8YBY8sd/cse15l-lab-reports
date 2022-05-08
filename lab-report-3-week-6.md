# Lab Report 3 Week 6

Implement all Group Choice Options (1-3) from Lab 5

## Streamlining ssh Configuration

> Show my .ssh/config file, and how I edited it (with VScode,
another program, etc)

Make a file named config, and then open it in VScode. Finally, copy and paste 
```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22zzz - (use your username)
```
into the file.

![.ssh/config file](https://8yby8sd.github.io/cse15l-lab-reports/configFile.png)

> Show the ssh command logging me into my account using just
the alias I chose.

Logging into my server with command `ssh ieng6`

![labReport3Part1Image2](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part1Image2.png)

> Show an scp command copying a file to my account using just the
alias I chose.

Using an `scp` command copying a file which named "labReport3Part1.txt" to my account using just the alias I chose.

![labReport3Part1Image3](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part1Image3.png)

---

## Setup Github Access from ieng6

> Show where the public key I made is stored on Github and in my user account (screenshot).

Open the public key file "id_rsa.pub" in VScode, and then copy and paste SSH public key to the Github SSH and GPG keys' "Key" field. 
You can find more resources from [Github Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

![labReport3Part2point1](https://8yby8sd.github.io/cse15l-lab-reports/sshKeyGithubpub.png)

> Show where the private key I made is stored on my user account (but not its contents) as a screenshot.

I changed the direction to the `.ssh` folder, and then I typed `ls` to list the files.

![labReport3Part2point2](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point2.png)

> Show running git commands to commit and push a change to
Github while logged into my ieng6 account.

First, use the `git clone <Github file link>` to clone the directory from the Github into the server. It should be look likes this:

![labReport3Part2point3image1](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point3image1.png)

After that, `git commit -m "<commands you want to write>"` to commit and `git push` to push a change to Github while logged into my ieng6 account.

![labReport3Part2point3.png](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point3.png)

> Link for the resulting commit.

[commit](https://github.com/8YBY8sd/markdown-parser/commit/4b335252254b9e03ea2206ea9fe9ee70b77b6a78)

---

## Copy whole directories with `scp -r`

> Show copying my whole markdown-parse directory to my ieng6 account.

I can use `scp -r . cs15lsp22@ieng6.ucsd.edu:~/markdown-parse` (add username after 22) to copying my whole markdown-parse directory to my ieng6 account.

![labReport3Part3p1.png](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part3p1.png)

> Show logging into my ieng6 account after doing this and compiling and running the tests for my repository.

After I log into my ieng6 account, type `ls` to see which directories have in my server. Then, change direction to `markdown-parse`. Finally, type "javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java MarkdownParse.java" and "java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"

![labReport3Part3point2](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part3point2.png)

> Show combining `scp`, `;`, and `ssh` to copy the whole directory and run the tests in one line.

```
scp -r *.java *.md lib ieng6:markdown-parse; ssh ieng6 "cd markdown-parse; /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac MarkdownParse.java; /software/CSE/oracle-java-17/jdk-17.0.1/bin/javac -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar MarkdownParseTest.java; /software/CSE/oracle-java-17/jdk-17.0.1/bin/java -cp .:lib/junit-4.13.2.jar:lib/hamcrest-core-1.3.jar org.junit.runner.JUnitCore MarkdownParseTest"
```

![labReport3Part3point3](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part3point3.png)