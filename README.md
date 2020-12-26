# git-experiments

Several git experiments to showcase cherry-pick, rebase, etc

## git squash
Use case: clean up you local commits before pushing to the remote branch
```
feature/counter -> commit 1 "some stuff"
feature/counter -> commit 2 "some similar stuff"
feature/counter -> commit 3 "some similar stuff I forgot"
```
Before pushing your commits you can do a interactive rebase:
`git rebase -i HEAD~3` opens the rebase of detached head

```
pick "some stuff"
pick "some similar stuff"
pick "some similar stuff I forgot"

pick "some stuff"
squash some similar stuff"
squash "some similar stuff I forgot"
```
save and continue rebase

select a commit message save and exit

## git cherry-pick
Use case: Include commits from other branches in your branch

```
feature/usefull-feature
feature/my-branch git cherry-pick hashcommitneeded
```
commit will be applied to `feature/my-branch` on top of current work

## git tag
Use case: Automatic deploymemt of defined tags
### List similar tags with:
```
$ git tag -l "v1.8.5*" or git tag (for all)
v1.8.5
v1.8.5-rc0
...
```
### Create and apply tags with
```
$ git tag -a v1.4 -m "my version 1.4"
$ git tag
v0.1
v1.3
v1.4
```
### Push tags
```
$ git push origin v1.5
Counting objects: 14, done.
Delta compression using up to 8 threads.
Compressing objects: 100% (12/12), done.
Writing objects: 100% (14/14), 2.05 KiB | 0 bytes/s, done.
Total 14 (delta 3), reused 0 (delta 0)
To git@github.com:schacon/simplegit.git
 * [new tag]         v1.5 -> v1.5
```
### Delete tags
```
$ git tag -d v1.4-lw
Deleted tag 'v1.4-lw' (was e7d5add)
```