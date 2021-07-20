# Error Resolving



#### 1. `git checkout [commit]`상태에서 본래 branch로 돌아갈때, `git checkout master`에서 Error 발생!

```bash
error: The following untracked working tree files would be overwritten by checkout:
...
...
(문제되는 파일 나열)
...
...
Please move or remove them before you switch branches.
Aborting
```



#### 해결 ==>> 

```bash
git fetch --all
git reset --hard [branch]
```



#### 2. `git push`에서 non-fast-forward 에러 발생 

```bash
! [rejected]	master -> master (non-fast-forward)
error: failed to push some refs to '[git address]'
hint: Updates were rejected because the tip of your current branch is behind
hint: its remote counterpart. Integrate the remote changes (e.g.
hint: 'git pull ...') before pushing again.
hint: See the 'Note about fast-forwards' in 'git push --help' for details. 
```

Git remote repository에 올라간 version이 최신이며, local에서 작업 중인 파일이 former version일 경우,

보통 **과거로 checkout이나 reset**을 했을 경우 **former version**으로 되돌려서 작업하고 **push하면 발생**한다.

(non-fast-forward는 흐름이 앞에 있지 않고 뒤에 있다는 뜻)



#### 해결 ==>>

```bash
git push origin +master
```