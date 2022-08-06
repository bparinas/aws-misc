# aws-misc

## securing aws /root/.aws/credentials (encrypt/decrypt sample below)

```
nullx@DESKTOP-4IHI081:/mnt/c/aws-vault$ cat credentials
[default]
aws_access_key_id = <access_key>
aws_secret_access_key = <secret_key>

nullx@DESKTOP-4IHI081:/mnt/c/aws-vault$ cat .phrase 
[replace this line with your strong passphrase and save in root homedir]

nullx@DESKTOP-4IHI081:/mnt/c/aws-vault$ gpg --output "credentials.gpg" --batch --passphrase-file .phrase --symmetric credentials
nullx@DESKTOP-4IHI081:/mnt/c/aws-vault$ cat credentials.gpg 
       qUEJVҦ\7z{
                 H_)bPZKMF@ M
QY:\,j[c4
        ۟Ć^|H2On-.JWjws(vcEHZ;L(J\/]\*zA[cxkI]iב"
nullx@DESKTOP-4IHI081:/mnt/c/aws-vault$ gpg --no-tty --batch --quiet --no-mdc-warning --passphrase-file .phrase --decrypt credentials.gpg
[default]
aws_access_key_id = <access_key>
aws_secret_access_key = <secret_key>
```
