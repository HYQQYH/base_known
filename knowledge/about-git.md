**base knowledge**
-------------
### Git知识

 1. Git push冲突的解决方法:(both modified)
 > 1.`git add xxx`
2.`git commit -m xx`
3.`git push  #! [rejected]        master -> master (fetch first)`
4.`git pull –rebase`
5.`git rebase –continue # examples/data/AI_industry/rules/rules.txt: needs merge,You must edit all merge conflicts and then mark them as resolved using git add`
6.`#merge file`
7.`git rebase –continue`
8.` if 7 fail: git rebase pull –rebase then 7`

 2. 从git里将jieba引入到服务器：
git clone https://github.com/fxsjy/jieba
mv jieba/ jieba_t
cp jieba_t/jieba jieba -r

 3. both modified:使用git diff手动merge
 4. 添加tag,`git tag V0.0.1`,`git push --tags`
  > 删除tag: git tag -d V0.0.1

 5. git add 之后git commit之前切勿git pull,否则git add的东西将会消失!
 6. git分支的新建与合并:https://git-scm.com/book/zh/v1/Git-%E5%88%86%E6%94%AF-%E5%88%86%E6%94%AF%E7%9A%84%E6%96%B0%E5%BB%BA%E4%B8%8E%E5%90%88%E5%B9%B6
 7. dev分支merge到master分支:
 > 在dev分支上运行 git rebase origin/master 把master的内容合并到dev.
 > 按提示进行修改