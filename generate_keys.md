# Generating Private & Public Keys

> SSL keys are used to confirm the identity of an entity. Generally, this would be used for server to server communication.

Most modern OS's come with the folder
`~/.ssh`
This is where the private and public keys are stored after they are generated.

To generate private keys you have to execute the following commands.
`ssh-keygen -t rsa -b 4096 -C "benjaminsnetwork@gmail.com"`
_This creates the key files, you will have an option to a passphrase. This is generally a good idea, if your OS was comprimised the attacker still needs the passphrase to pretend to be you to other servers_
