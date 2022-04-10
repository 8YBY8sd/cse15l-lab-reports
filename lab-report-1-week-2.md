# Lab Report 1 Week 2

>Installing VScode

Go to the [Visual Studio Code website](https://code.visualstudio.com/), 
![Image](https://8yby8sd.github.io/cse15l-lab-reports/vswebsite.png)
and follow the instructions to download and install it on your computer. There are versions for all the
major operating systems, like OSX (for Macs) and Windows (for PCs).

After you complete installtion, you should be able to open a window that looks like this (it might
have different colors, or a different menu bar, depending on your system and settings)

![Image](https://8yby8sd.github.io/cse15l-lab-reports/Screenshot%202022-04-07%20174231.png)	

---	
>Remotely Connecting

First, you should install a program called OpenSSH,
which is a program that can connect your computer to other computers: go to [this](https://docs.microsoft.com/en-us/windows-server/administration/openssh/openssh_install_firstuse) website, and then you can follow these steps show in this picture blow.![Image](https://8yby8sd.github.io/cse15l-lab-reports/OpenSSH.png)

Then, look up your course-specific account for CSE15L here:
https://sdacs.ucsd.edu/~icc/index.php

After you get your account, go to Visual Studio Code and open a termainal (Ctrl + `, or use the Terminal → New
Terminal menu option). Your command will look like this, but with the zz replaced by the letters in your course-specific account.

```
$ ssh cs15lsp22zz@ieng6.ucsd.edu
```

(That’s one, five, l (lowercase L))

Since this is first time you’ve connected to this server, you will probably get a message like this:
```
⤇ ssh cs15lsp22zz@ieng6.ucsd.edu

The authenticity of host 'ieng6.ucsd.edu (128.54.70.227)' can't
be established.

RSA key fingerprint is
SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.

Are you sure you want to continue connecting
(yes/no/[fingerprint])?
```

Say yes to these messages when you are connecting to a new server for the first time; it’s expected to get this message in that case.

So type yes and press enter, then give your password; the whole interaction should look something like this once you give your password and are logged in:

```
⤇ ssh cs15lsp22zz@ieng6.ucsd.edu

The authenticity of host 'ieng6-202.ucsd.edu (128.54.70.227)' can't be established.

RSA key fingerprint is SHA256:ksruYwhnYH+sySHnHAtLUHngrPEyZTDl/1x99wUQcec.

Are you sure you want to continue connecting (yes/no/[fingerprint])?

Password:

Last login: Sun Jan 2 14:03:05 2022 from 107-217-10-235.lightspeed.sndgca.sbcglobal.net
quota: No filesystem specified.
Hello cs15lsp22zz, you are currently logged into
ieng6-203.ucsd.edu


You are using 0% CPU on this system
Cluster Status

Hostname Time #Users Load Averages

ieng6-201 23:25:01 0 0.08, 0.17, 0.11

ieng6-202 23:25:01 1 0.09, 0.15, 0.11

ieng6-203 23:25:01 1 0.08, 0.15, 0.11

Sun Jan 02, 2022 11:28pm - Prepping cs15lsp22
```

If you're not the first time to connect this server, your terminal should look something similar to this after you enter the password:![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshlogin.png)

Now your terminal is connected to a computer in the CSE basement, and any commands you run will run on that computer! We call your computer the client and the computer in the basement the server based on how you are connected.

>Trying Some Commands

Try running the commands a few times in different ways, both on your computer, and on the remote computer after ssh-ing. Here is some examples:
```
cd ~
cd
ls -lat
ls -a
```

You'll get something similar to this picture:![Image](https://8yby8sd.github.io/cse15l-lab-reports/sshcode.png)

---	
>Moving Files with scp

First, you need to creat a file on your computer called ```WhereAmI.java``` which include these code:
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


---	
>Setting an SSH Key


---	
>Optimizing Remote Running

