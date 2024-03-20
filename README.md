# gitskills
this is a repository for git-learning 修改
Creating a new branch is quick.
this is dev version branch.
Creating a new branch is quick and simple.
a new change
a new change for bug branch，修复了main分支中的bug（由issue分支合并过去）不代表dev中的bug也被同步修复，仍然会处于之前的水平。为了在不提交当前修改至当前分支，stash可以方便快速切换到另一个分支
/*如果dev在修改前与main是保持同步的，其实可以直接用stash后的dev，然后修改bug完merge no ff去main，但如果dev本身就已经是main的先前版本，改bug只能在main分支的基础上引出新分支修改，那意味着issue做的工作，dev还需要重新做一次，在stash pop后做修改哦；并且要选择好apply的stash*/
在master分支上修复了bug后，我们要想一想，dev分支是早期从master分支分出来的，所以，这个bug其实在当前dev分支上也存在。
那怎么在dev分支上修复同样的bug？重复操作一次，提交不就行了？
有木有更简单的方法？
有！
同样的bug，要在dev上修复，我们只需要把4c805e2 fix bug 101这个提交所做的修改“复制”到dev分支。注意：我们只想复制4c805e2 fix bug 101这个提交所做的修改，并不是把整个master分支merge过来。
为了方便操作，Git专门提供了一个cherry-pick命令，让我们能复制一个特定的提交到当前分支：
记住之前issue的标识，从main回到dev后直接cherry-pick这个标识，那么dev本身就是直接会更新版本，并且-m的操作描述也是和issue一致的，然后再stash pop，