# git-ssh-keygen
添加 SSH KEY

#首先需要检查你电脑是否已经有 SSH key     
```
$ ls ~/.ssh
```
>id_dsa.pub   
>id_ecdsa.pub   
>id_ed25519.pub    
>id_rsa.pub    

#创建一个 SSH key
```
$ ssh-keygen -t rsa -C "your_email@example.com"
```  
代码参数含义：       
-t 指定密钥类型，默认是 rsa ，可以省略。          
-C 设置注释文字，比如邮箱。            
-f 指定密钥文件存储文件名。     

#将创建的 ssh key 添加到git上       

#测试
```
$ ssh -T git@github.com
```
如报以下错误      
```
ssh: connect to host github.com port 22: Connection timed out
```
##解决办法
```
$ cd ~/.ssh/ && touch config
```

可以把以上内容拷到config文件里面，注意修改你的邮箱，保存并关闭

```
Host github.com
User xxx@163.com （你注册github时的邮箱，这里使用注册的用户名也行）
Hostname ssh.github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa
Port 443
```
进行测试是否连接上github.com 
```
ssh -T git@github.com
The authenticity of host ‘[ssh.github.com]:443 ([207.97.227.248]:443)’ can’t be established.
RSA key fingerprint is 16:27:ac:a5:76:28:2d:36:63:1b:56:4d:eb:df:a6:48.
Are you sure you want to continue connecting (yes/no)? y
Please type ‘yes’ or ‘no’: yes
Warning: Permanently added ‘[ssh.github.com]:443,[207.97.227.248]:443’ (RSA) to the list of known hosts.
Hi zhou411424! You’ve successfully authenticated, but GitHub does not provide shell access.
出现Hi xxx!……表示连接成功。
```

# git commit里面记录的帐号，与你的帐号不一致

1.先配置 git config --global user.name aaaa
      git config --global user.email aaaa@163.com
2.使用以下命令 修改commit 信息：
```
$ git commit --amend --reset-author

```
