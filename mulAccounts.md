## 生成个人账户ssh-keygen
```
ssh-keygen -t rsa -f ~/.ssh/id_rsa.fuyongfan
```
## 为各账户配置config 文件
```
cd ~/.ssh
vi config
```
- 文件中添加以下参数
```
# 当访问 https://github.com 地址时 账户名为 fuyongfan 私钥 文件为 ~/.ssh/id_rsa.fuyongfan
Host https://github.com
User fuyongfan
IdentityFile ~/.ssh/id_rsa.fuyongfan

# 当访问 icode.baidu.com 地址时 账户名为 fuyongfan 私钥 文件为 ~/.ssh/id_rsa.fuyongfan
Host icode.baidu.com
User fuyongfan01
IdentityFile ~/.ssh/id_rsa.fuyongfan01
```
## 添加公钥， 
- github 添加完公钥时 使用命令  ssh -T git@github.com 测试并激活ssh