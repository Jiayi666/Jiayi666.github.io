---
layout:     post
title:      "Fix conflicts in Git push"
subtitle:   "especially when a branch is behind"
date:       2016-07-05	17:10:00
author:     "Jiayi.Liu"
header-img: "img/post-bg-2015.jpg"
catalog: 	true
tags:
    - Git
---

### Conflicts in Git push/merge

When we want to merge two branches, conflicts may come up because those two branches has edited the same file since their departure. (see. [解决冲突](http://www.liaoxuefeng.com/wiki/0013739516305929606dd18361248578c67b8067c8c017b000/001375840202368c74be33fbd884e71b570f2cc3c0d1dcf000))

In our daily use, conflicts offten happens when the user `reset` his/her local repository and make adaptation (let's just focus on one file, or fast-forward won't get wrong), so his local repository is behind the remote one and also has changed the same file, thus a conflict will be generated.

### Fix the conflicts

If there is a conflict between remote repo and the local repo, when you type `git push origin master`, Git will tell you that your local repo is behind, and you need to pull first. Once you pull, Git will automatically **mark out** where specifically the conflicts locate. Git will change the conflicted file into structure like this:
<pre>
		Git is a distributed version control system.
		Git is free software distributed under the GPL.
		Git has a mutable index called stage.
		Git tracks changes of files.
		<<<<<<< HEAD
		Creating a new branch is quick & simple.
		=======
		Creating a new branch is quick AND simple.
		>>>>>>> feature1
</pre>

Here Git intend to make you **take choice**, what you need to do is to **tell it the final decision**.

The only thing we need to do is **edit the conflicted file again**, once we made changes, we can do `git add...`, `git commit...` again. So both branches goes ahead one step, so just like this graph, those two branch/repo can be compatible again.
<pre>
		$ git log --graph --pretty=oneline --abbrev-commit
		*   59bc1cb conflict fixed
		|\
		| * 75a857c AND simple
		* | 400b400 & simple
		|/
		* fec145a branch test
		...
</pre>