# git-cookbook(working in progress)
git cookbook, git烹饪书, 实用git技巧

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
