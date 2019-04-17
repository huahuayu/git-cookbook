# git-cookbook(working in progress)
git cookbook, git烹饪书, 实用git技巧
## 连接远程repo
### Existing folder
```
cd existing_folder
git init
git remote add origin git@git/remote/repo.git
git add .
git commit -m "Initial commit"
git push -u origin master
```

### Existing Git repository
```
cd existing_repo
git remote rename origin old-origin
git remote add origin git@git/remote/repo.git
git push -u origin --all
git push -u origin --tags
```

## 实用技巧
### git status中文显示问题
git status中文显示为8进制编码，如果要正常显示，可使用命令`git config --global core.quotepath false`即可  
``` zsh
shiming@pro ➜  algorithm git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   "\351\235\242\350\257\225\347\234\237\351\242\230/\345\205\224\345\255\220\347\271\201\346\256\226/solution.go"
	new file:   "\351\235\242\350\257\225\347\234\237\351\242\230/\345\205\224\345\255\220\347\271\201\346\256\226/solution_test.go"
	new file:   "\351\235\242\350\257\225\347\234\237\351\242\230/\345\256\236\347\216\260\346\240\210\346\225\260\346\215\256\347\273\223\346\236\204/solution.go"

shiming@pro ➜  algorithm git:(master) ✗ git config --global core.quotepath false
shiming@pro ➜  algorithm git:(master) ✗ git status
On branch master
Your branch is up to date with 'origin/master'.

Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   面试真题/兔子繁殖/solution.go
	new file:   面试真题/兔子繁殖/solution_test.go
	new file:   面试真题/实现栈数据结构/solution.go
```

### 回退操作
**场景一：**    
文件已经commit，甚至push，现在希望以后不再跟踪，且要从repo中删除。   
首先将文件添加到`.gitignore`然后执行以下命令。  
```
$ git rm --cached <file-name>
# 支持通配符
$ git rm --cached *.log
```

如果是文件夹  
```
$ git rm -r --cached directory/
```

`git rm --cached <file-name>`会使文件不再被跟踪，但不会删除本地文件；`git rm -f <file-name>`还会将本地文件都删除掉  

**场景二：**  
文件已经添加到stage，还未commit，但暂时不想提交，想从staged状态变为unstaged状态，文件变更不丢失。  
```
# unstage一个文件
$ git reset HEAD <file-name>
# unstage所有文件
$ git reset HEAD .
```

**场景三：**  
放弃当前所有变更，回退到上一个commit版本  
```
$ git reset --hard
```

放弃所有变更，回退到指定版本
```
$ git reset --hard <commit-id>
```

**场景四：**  
放弃已经track的，但是没有在stage的文件变更，已经在stage的文件保持不变(比`git reset --hard`要安全)   
```
# 单个文件
$ git checkout -- <file-name>
# 所有文件
$ git checkout -- .
```

### commit msg
可以设定git hooks对commit msg做格式检查，如果设定了检查后不想校验可以使用 `git commit` with `--no-verify` option 
参考：https://stackoverflow.com/questions/39963695/how-to-remove-git-hooks   
