# generacion de llaves SSH

# Paso 1

ssh-keygen -t ed25519 -C "your_email@example.com"

> Generating public/private ALGORITHM key pair. 
> Enter a file in which to save the key (/Users/YOU/.ssh/id_ALGORITHM): github [Press enter] 
> Enter passphrase (empty for no passphrase): Escribe contraseña [Press enter] 
> Enter same passphrase again: Escribe contraseña otra vez [Press enter] 

# Paso 2

eval "$(ssh-agent -s)"
> Agent pid 59566

# Paso 3

touch ~/.ssh/config
code config

[Se abre VScode y pegas lo que esta debajo↓]

Host github.com
  AddKeysToAgent yes
  UseKeychain yes
  IdentityFile ~/.ssh/github

> [Command + S para guardar cambios] 

# Paso 4

ssh-add --apple-use-keychain ~/.ssh/github

# Paso 5 

pbcopy < ~/.ssh/github.pub

[Ir a Github y pegar la llave]

# Paso 6

ssh -T git@github.com

> The authenticity of host 'github.com (IP ADDRESS)' can't be established.
> ED25519 key fingerprint is SHA256:+DiY3wvvV6TuJJhbpZisF/zLDA0zPMSvHdkr4UvCOqU.
> Are you sure you want to continue connecting (yes/no)? yes [Press enter]

> Hi USERNAME! You've successfully authenticated, but GitHub does not
> provide shell access.



