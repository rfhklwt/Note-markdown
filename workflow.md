先保存好你新添加的代码。在 git bash 里你当前的文件夹应该是类似这样
```
$ git remote -v
origin	https://github.com/rfhklwt/LeetCode.jl.git (fetch)
origin	https://github.com/rfhklwt/LeetCode.jl.git (push)
```
1. 添加`JuliaCN`，把名字记为`upstream: git remote add upstream https://github.com/JuliaCN/LeetCode.jl.git`
2. 拉取`upstream`的信息`git fetch upstream`
3. 用`upstream`重置当前文件夹`git reset --hard upstream/master`
4. 重置`rfhklwt:master: git push -f origin master -- `这一步通过`force push`来进行重置
5. 把新添加的代码重新填进来，然后按照正常流程做