# Lab Report 3 Week 6

Implement all Group Choice Options (1-3) from Lab 5

> Streamlining ssh Configuration

- Make a file named config, and then open it in VScode. Finally, copy and paste 
```
Host ieng6
    HostName ieng6.ucsd.edu
    User cs15lsp22zzz - (use your username)
```
into the file.

![.ssh/config file](https://8yby8sd.github.io/cse15l-lab-reports/configFile.png)

- Logging into my server with command `ssh ieng6`

![labReport3Part1Image2](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part1Image2.png)

- Using an `scp` command copying a file which named "labReport3Part1.txt" to my account using just the alias I chose.

![labReport3Part1Image3](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part1Image3.png)


> Setup Github Access from ieng6

- Open the public key file "id_rsa.pub" in VScode, and then copy and paste SSH public key to the Github SSH and GPG keys' "Key" field. 
You can find more resources from [Github Docs](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

![labReport3Part2point1](https://8yby8sd.github.io/cse15l-lab-reports/sshKeyGithubpub.png)

- Show where the private key I made is stored on my user account (but not its contents) as a screenshot.

I changed the direction to the `.ssh` folder, and then I typed `ls` to list the files.

![labReport3Part2point2](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point2.png)

- First, use the `git clone <Github file link>` to clone the directory from the Github into the server. It should be look likes this:![labReport3Part2point3image1](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point3image1.png)

After that, `git commit -m "<commands you want to write>"` to commit and `git push` to push a change to Github while logged into my ieng6 account.

![labReport3Part2point3.png](https://8yby8sd.github.io/cse15l-lab-reports/labReport3Part2point3.png)

- Link for the resulting commit.
https://github.com/8YBY8sd/markdown-parser/commit/4b335252254b9e03ea2206ea9fe9ee70b77b6a78

> Copy whole directories with `scp -r`

Show copying my whole markdown-parse directory to my ieng6 account.

![labReport3Part3point1.png]()

Show logging into my ieng6 account after doing this and compiling and running the tests for my repository.

![]()

Show combining `scp`, `;`, and `ssh` to copy the whole directory and run the tests in one line.