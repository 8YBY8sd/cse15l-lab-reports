# Lab Report 1 Week 2

**[Welcome!](https://youtu.be/dQw4w9WgXcQ)**

>Installing VScode

Go to the [Visual Studio Code website](https://code.visualstudio.com/), 
![Image](https://8yby8sd.github.io/cse15l-lab-reports/vswebsite.png)
and download and install it on your computer. 

After you complete installtion, you should be able to open a window that looks like this (it might
have different colors, or a different menu bar, depending on your system and settings)

![Image](https://8yby8sd.github.io/cse15l-lab-reports/Screenshot%202022-04-07%20174231.png)	

---	
>Remotely Connecting

First, you should install a program called OpenSSH,
which is a program that can connect your computer to other computers: go to [this](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) website, and then you can follow these steps show in this picture blow.![Image](https://8yby8sd.github.io/cse15l-lab-reports/OpenSSH.png)

Then, look up your course-specific account for CSE15L here:
https://sdacs.ucsd.edu/~icc/index.php

If you forgot your password, here is document teaches you [How to reset your password](https://8yby8sd.github.io/cse15l-lab-reports/How-to-Reset-your-Password.pdf).

After you get your account, go to Visual Studio Code and open a termainal (Ctrl + `, or use the Terminal → New Terminal menu option). Your command will look like this, but with the aub replaced by the letters in your course-specific account.

```
$ ssh cs15lsp22aub@ieng6.ucsd.edu
```

(That’s one, five, l (lowercase L))

Since this is first time you’ve connected to this server, you will probably get a message like this:
```
⤇ ssh cs15lsp22aub@ieng6.ucsd.edu

The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't be established.

RSA key fingerprint is
SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.

Are you sure you want to continue connecting
(yes/no/[fingerprint])?
```

Say yes to these messages when you are connecting to a new server for the first time.

So type yes and press enter, then give your password; the whole interaction should look something like this once you give your password and are logged in:

```
⤇ ssh cs15lsp22aub@ieng6.ucsd.edu

The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.

RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.

Are you sure you want to continue connecting (yes/no/[fingerprint])?

Password:

Last login: Sun Jan 2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lsp22aub, you are currently logged into
ieng6-203.ucsd.edu


You are using 0% CPU on this system
Cluster Status

Hostname Time #Users Load Averages

ieng6-201 23:25:01 0 0.08, 0.17, 0.11

ieng6-202 23:25:01 1 0.09, 0.15, 0.11

ieng6-203 23:25:01 1 0.08, 0.15, 0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lsp22
```

If you're not the first time to connect this server, your terminal should looks like this after you enter the password:![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshlogin.png)

Now your terminal is connected to server.

>Trying Some Commands

Try running the commands a few times in different ways, both on your computer, and on the remote computer after ssh-ing. Here is some examples:
```
cd ~
cd
ls -lat
ls -a
```

You'll get something looks like this picture:![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshcode.png)

---	
>Moving Files with scp

Okay! Let's try to moving a file from your computer to server.

First, you need to creat a file on your computer. Here I make it called ```WhereAmI.java``` which include these code:
```
class WhereAmI {
    public static void main(String[] args) {
        System.out.println(System.getPropert("os.name"));
        System.out.println(System.getPropert("user.name"));
        System.out.println(System.getPropert("user.home"));
        System.out.println(System.getPropert("user.dir"));
    }
}
```

Then, in the terminal from the directory where you made this file, run this command.

```
scp WhereAmI.java cs15lsp22aub@ieng6.ucsd.edu:~/
```
Then, log into server with ssh again, and use ls. You should see something looks like this:![Image](https://8yby8sd.github.io/cse15l-lab-reports/scpWhereAmI.png)

---	
>Setting an SSH Key

Let's set a ssh keys to save your life. If you have ssh keys, you don't need to enter the password every single time. 

Let me show you some magic:
```
# on client (your computer)
$ ssh-keygen
Generating public/private rsa key pair.
Enter file in which to save the key
(/Users/<user-name>/.ssh/id_rsa): /Users/<user-name>/.ssh/id_rsa
Enter passphrase (empty for no passphrase):
```
Note: Make sure that you do not add a paraphrase for these step.
```
Enter same passphrase again:
Your identification has been saved in
/Users/<user-name>/.ssh/id_rsa.
Your public key has been saved in
/Users/<user-name>/.ssh/id_rsa.pub.
The key fingerprint is:
SHA256:jZaZH6fI8E2I1D35hnvGeBePQ4ELOf2Ge+G0XknoXp0
<user-name>@<system>.local
The key's randomart image is:
+---[RSA 3072]----+
| |
| . . + . |
| . . B o . |
| . . B * +.. |
| o S = *.B. |
| = = O.*.*+|
| + * *.BE+|
| +.+.o |
| .. |
+----[SHA256]-----+
```

This created two new files on your system; the private key (in a file id_rsa) and the public key (in a file id_rsa.pub), stored in the .ssh directory on your computer.
Now we need to copy the public key to the .ssh directory of your user account on the server.
```
$ ssh cs15lsp22aub@ieng6.ucsd.edu
<Enter Password>
# now on server
$ mkdir .ssh
$ <logout>
# back on client
$ scp /Users/<user-name>/.ssh/id_rsa.pub cs15lsp22aub@ieng6.ucsd.edu:~/.ssh/authorized_keys
# You use your username and the path you saw in the command above
```

Once you do this, you should be able to ssh or scp from this client to the server without entering your password.

Here is how is that looks like when you ssh from the client to the server without entering your password:![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshloginwithoutpw.png)

---	
>Optimizing Remote Running

Try to write less steps and do more work.
Here're some hints:

1.  You can write a command in quotes at the end of an ssh command to directly run it on the remote server, then exit.
![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshcom.png)

2. You can use semicolons to run multiple commands on the same line in terminals.


# Thank You For Look My Blog Post
Work Cited: https://docs.google.com/document/d/1AO6RDoJnaWxMui-UFjEa_2bbQ4qcANpbIpPuV-awsOg/edit#heading=h.z99msbqf07rq
