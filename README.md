## Set up git on Windows :octocat:

### Installing Git
Download the installer for Windows from the Git [official site](https://git-scm.com/download/).

Git for Windows comes with Git Bash (it's own command prompt), and it looks better than Windows default prompt. 

### Set up git 

- First we need creates a new ssh key, using the provided email as a label. Open Git Bash after installation and type: 
```
$ ssh-keygen -t rsa -b 4096 -C "your_email@domain.com"
```
It will return: 
```
Generating public/private rsa key pair.  
Enter file in which to save the key (/Users/you/.ssh/id_rsa): [Press enter]
```
Press Enter. This accepts the default file location.

Then he asks for a password. This password will have to be typed every time you download something from a repository or send something there. You can leave it blank. This is your choice. If you want to leave without, just enter. If not, enter the password and confirm.
```
Enter passphrase (empty for no passphrase): [Type a passphrase]  
Enter same passphrase again: [Type passphrase again]
```
It will return a confirmation: 
```
Your identification has been saved in /Users/you/.ssh/id_rsa.  
# Your public key has been saved in /Users/you/.ssh/id_rsa.pub.
# The key fingerprint is:
# 01:0f:f4:3b:ca:85:d6:17:a1:7d:f0:68:9d:f0:a2:db your_email@domain.com
```
- Start the ssh-agent in the background. Let's activate it:
```
$ exec ssh-agent bash [Press enter]
$ eval ssh-agent -s [Press enter]
```
It will return something like that: 
```
SSH_AUTH_SOCK=/tmp/ssh-9S2E7m94sl07/agent.18936; 
export SSH_AUTH_SOCK;
SSH_AGENT_PID=18172; 
export SSH_AGENT_PID;
echo Agent pid 18172;
```
- Add your SSH key to the ssh-agent:
```
$ ssh-add ~/.ssh/id_rsa [Press enter]
```
It will return: 
```
Identity added: /c/Users/you/.ssh/id_rsa (your_email@domain.com)
```
- Copies your SSH key to your clipboard
```
$ cat ~/.ssh/id_rsa.pub > /dev/clipboard 
```

2. Logged into your GitHub account, go to the top right options, click your profile picture:

`Settings > SSH and GPG Keys > New SSH Key`

Give a title to your key, and past the key int the blank large box.

## Testing if your configuration is correct
Still on Git Bash: 
```
$ ssh -T git@github.com
```
It will return: 
```
Hi username! You've successfully authenticated, but GitHub does not provide shell access.
```
Then everything is correct!

Now anytime you clone a repository, GitHub will automatically give you the `SSH URL` and you will have to provide your `SSH key` paraphrase anytime you push and pull changes and you will not need to type in your username or your password anymore. 
