## clone 分支：
1. git clone git@github.com:tom-li-520/tom-li-520.github.io.git
2. cd tom-li-520.github.io.git

## 生产&部署
hexo clean && hexo g && hexo d

## 修改:

1. 切换到hexo分支：git checkout hexo
2. 添加所有更改：git add .
3. 提交更改：git commit -m "message"
4. 推送到远程的hexo分支：git push origin hexo

## 新环境需要
 npm install hexo-deployer-git --save
 
 # 禁用自动换行符转换（所有仓库生效） 解决本地部署和github上显示不一致问题
git config --global core.autocrlf false 

