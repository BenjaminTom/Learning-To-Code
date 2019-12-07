# Generating Private & Public Keys

> SSL keys are used to confirm the identity of an entity. Generally, this would be used for server to server communication.

Most modern OS's come with the folder

```
~/.ssh
```

This is where the private and public keys are stored after they are generated.

To generate private keys you have to execute the following commands.

```
ssh-keygen -t rsa -b 4096 -C "your_email@gmail.com"
```

_This creates the key files, you will have an option to add a passphrase. This is generally a good idea, if your OS was comprimised the attacker still needs the passphrase to pretend to be you to other servers._

For this example, i'll make a set of keys titles `id_rsa_github`

After this is complete you will have the two files created within the `./shh` folder.
One of these new files will have the suffix `id_rsa_github.pub` This file contains the key you want to share with the world.

Depending on what type of operating system you have, you can copy its contents a few different ways.

**MAC**

```
pbcopy < ~/.ssh/id_rsa_github.pub
```

**UBUNTU**
_Using Digital Ocean_

```
cat ~/.ssh/id_rsa_github.pub
```

> This will reveal the contents of the file, from here you can just copy and paste

Next you must tell your computer to identify as a private key. To cheack the current identity of your computer run

```
ssh-add -l
```

If you're using ubuntu you also have to add an SSL agent before adding an identity

```
eval `ssh-agent -s`
```

and then

```
ssh-add
```

```
ssh-add id_rsa_github
```

**Conclusion**

This process documents how to generate key sets and then copy the public key to your clipboard. This public key can then be pasted into clients to set up SSH connections. This is handy for communicating to servers without being prompted for a password and/or email address.

From here you also have the public key you just generated added to your clipboard. You can go ahead and add this to github by clicking your profile icon in the top RHS corner and clicking settings. In settings go to SSL and add a a new key.

Now you can run

```
git clone git@github.com:BenjaminTom/repo_name
```

and it will copy the contents of the repo to your computer, without you having to log in.
