---
title: '夜天之书 #23 Merge GitHub Repositories'
---

这几周写了几篇长文，一下子就找不到日签的感觉了，日签还是有一两个点就可以写的。

比如最近 TiDB 社区连续的几个往 MonoRepo 方向走的合并卫星项目的提案，就挺有意思的。

* [Proposal: Move parser back to pingcap/tidb](https://internals.tidb.io/t/topic/385)
* [Proposal: Merge BR repo into TiDB](https://internals.tidb.io/t/topic/256)
* [Proposal: Merge Dumpling repo into TiDB](https://internals.tidb.io/t/topic/434)
* [Proposal: Merge DM repo into TiCDC](https://internals.tidb.io/t/topic/461)

这里面涉及复杂的 Git 技巧，我简单讲一讲。

介绍之前，想起来之前写过一篇旧文是关于 Git Workflow 的，如果有想看的同学可以评论说一声，要是有人想看我就抽时间改改表达再发出来。

另外，王垠在[《关于 Git 的礼节》](http://www.yinwang.org/blog-cn/2015/03/11/git-etiquette)一文里对 Git 的评价大抵是有点道理的。我介绍这些技巧是为了改善生活，但是衷心希望你并不需要知道这些内容。

相关的 Git 技巧都是在合并 GitHub 代码仓库的时候碰到问题探索出来的。

要把一个仓库合并到另一个仓库，却要保持原来的提交历史，以供开发者阅读索引，而不是只合并文件，一个大 commit 撸进来，应该怎么办呢？为了方便，我们把合并的两个仓库分别成为主仓库和子仓库，子仓库合并进主仓库。

这个问题的解法根据不同需要会不太相同。一种流行和推荐的一个仓库依赖另一个仓库的方式是以 [git-submodule](https://git-scm.com/book/en/v2/Git-Tools-Submodules) 来在主仓库保留子仓库的一个连接。这种方式尤其受到需要 vendor 三方依赖的 C/C++ 项目的青睐，例如 ClickHouse 就是重度 git-submodule 用户。

但是 git-submodule 会导致实际存在两个 git repo 或者说两份不同 .git 目录下的元数据，这对于 TiDB 社区所期待的直接做实质合并是有出入的。换句话说，git-submodule 带来的好处实际上是上述方案当中的短处。

可以采用一个比较冷门的命令 [git-subtree](https://www.atlassian.com/git/tutorials/git-subtree) 来​合并两个仓库，这个命令在合并两个仓库时大致的过程如下。

```bash
git checkout -b merge-dumpling
git subtree add --prefix=dumpling https://github.com/pingcap/dumpling.git master
```

好，结束了。

如果你在 TiDB 的根目录下执行这个命令，你就会在新建的 dumpling 子目录下看到 pingcap/dumpling 仓库的内容被带过来了，连同保持 commit hash 值的，文件路径稍有改动的提交历史都会出现在原本的提交历史当中。

注意到这时候的 merge-dumpling 相比起一个干净可合并的分支还有几个方向上的距离，我们一个一个来解决。

第一个问题是 git-subtree 命令带过来的提交历史是按照自己的时间顺序插入到主仓库的提交历史当中的，这样是无法在 merge 到主仓库主分支的时候保持线性历史的，除非 force push 到主分支上，而 force push 是一个危险动作，通常被禁止。

我们并不需要完全保留原来的时间，只需要保留 diff 的 commit 本身来做 blame 即可。所以我们基于 master 分支运行 [git-rebase](https://git-scm.com/book/en/v2/Git-Branching-Rebasing) 命令来解决这个问题。

```bash
git rebase master
```

第二个问题是 GitHub 上的提交，如果是通过 Pull Request 提交的，默认 GitHub 会生成一个形如 `(#1234)` 的后缀。这个对应到主仓库编号为 #1234 的 Pull Request 上。但是现在两个代码仓库合并，这个编号就会错误的指向新仓库相同编号的 issue 或 pull request 了。

为了解决这个问题，我们需要批量的修改合并过程中引入的 commit 的 commit message 内容。我们可以使用 [git-filter-branch](https://git-scm.com/docs/git-filter-branch) 命令来修改。这个命令就是一个非常冷门的复杂命令，希望你一辈子也不用跟它打交道。

```bash
git filter-branch --msg-filter 'perl -pe "s/#(\d+)/pingcap\/dumpling#\$1/"' -- HEAD...master
```

藉由一个简单的查找替换和 [git-rev-list](https://git-scm.com/docs/git-rev-list) 式的 commit 筛选方法，我们改好了这堆提交历史。

最后一个问题，也是最麻烦的问题，是 git-subtree 合并两个仓库后，子仓库带来的提交历史的文件路径和合并后的文件路径有差别。

例如，dumpling 仓库有一个 commit 修改了 tests 文件夹下的文件，上述 git-subtree 合并之后相关的文件被移动到了 dumpling/tests 下，但是 commit 里的 diff 还是 tests 路径。这会导致 [git-blame](https://git-scm.com/docs/git-blame) 不可用，因为新的 dumpling 目录下的文件将会没有历史，只有合并的那个 commit 的历史。虽然子仓库的提交历史都还在，但是路径是错的。

为了解决这个问题，逻辑上讲很简单。同上列出相关的提交历史，修改其中文件的相对路径，加上 dumpling 前缀即可。

但是实际上 git 支持的命令比较神秘，我能找到的最好的做法要回到 git-subtree 操作之前去修复。至少我没有找到在 git-subtree 合并后仅修改子仓库 commit 相关的文件路径的好办法。

回到 git-subtree 操作之前的意思是，我们首先准备好一个所有文件都在 dumpling 目录下的子仓库分支，这里我们可以修改全部 commit 的文件相对路径。然后再通过 git-subtree 合并仓库，最后做一些清理工作。

具体流程如下。

```bash
git clone https://github.com/pingcap/dumpling.git
cd dumpling
git checkout -b merge-to-tidb
git filter-branch --tree-filter 'mkdir -p dumpling && ls -A | grep -v dumpling | xargs -I files mv files dumpling/' -- HEAD
git filter-branch --msg-filter 'perl -pe "s/#(\d+)/pingcap\/dumpling#\$1/"' -- HEAD
git push
```

随后在 tidb 目录下

```bash
git checkout -b merge-dumpling
git subtree add --prefix=dumpling https://github.com/tisonkun/dumpling.git merge-to-tidb
cd dumpling
mv dumpling/* .
mv dumpling/.* . # move hidden files
git add .
git commit --amend -s
git push
```

这么一通搞就能把文件相对路径也修复了，成果可以看 [merge-dumpling](https://github.com/tisonkun/tidb/commits/merge-dumpling) 分支。

可以看到解决第三个问题比较笨拙，各个命令之间配合得也不是很好，不过我是没找到更好的办法了。据说 [git-filter-repo](https://github.com/newren/git-filter-repo) 是一个现代的解决方案，但是这个东西要额外下载，看文档也挺复杂的，遂放弃。如果有更好的解决方案，欢迎下方评论交流。

写到这里正好跟 pingcap/parser 合并的 driver @xhebox 聊了一下，上面这个过程里 git-subtree 的过程可以简化成直接把第一步 dumpling 整完的内容 push 到 tidb 的一个分支上，然后直接 rebase 到 tidb 的 master 分支上去。这有点脑筋急转弯，不过确实省了一个 git-subtree 命令和后续手动减少一层目录的工作量。
