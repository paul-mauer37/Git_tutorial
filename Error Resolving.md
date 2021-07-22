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



#### 3. `git push`에서 fetch first 에러 발생 (https://stackoverflow.com/questions/28429819/rejected-master-master-fetch-first)

2번과 유사 에러

(`.git`을 삭제했다 다시 설치했을때, 기존 github에 푸시된 파일과 푸시하려는 파일이 다를 경우 발생)

Probably somebody else has pushed to master already, and your commit is behind. Therefore you have to fetch, merge the changeset, and then you`ll be able to push again.



#### 해결 ==>>

```bash
git fetch origin master
git merge origin master
```

이때, non-fast-forward에러가 발생한다면,

```bash
git fetch origin master:tmp
git rebase tmp
git push origin HEAD:master
git branch -D tmp
```



#### 4. Error: GH001: Large files detected. Github의 file size limit인 100MB를 초과할 경우 발생

```bash
remote: error: GH001: Large files detected. You may want to try Git Large File Storage - https://git-lfs.github.com.
remote: error: Trace: [문자열(commit에 관한 것으로 추정)]
remote: error: ...
remote: error: File [File Name] is [File Size]; this exceeds GitHub`s file size limit of 100.00MB
To [Remote Repository Address]
![remote rejected] master -> master (pre-receive hook declined)
error: failed to push some refs to '[Remote Repository Address]'
```



#### 해결 ==>> GIT LFS(Large File Storage)

```bash
git lfs install

*** git lfs를 이용해서 track 해야한다. git add로 staging 할 경우 동일 오류 발생.
또한, 한번 staging된 파일은 git history에 남아있으므로 git lfs를 이용하기 위해서는 staging되지 않아야 한다. 만약 history에 남았을 경우, .git파일을 삭제하고 다시 설치해야 한다.

git lfs track "[File Name]"		// 단일 파일 track
git lfs track "*.확장자"		  // 동일 확장자 파일 전체 track

이후 전체 부분 git add를 이용해 staging해서 remote repository에 push할 경우, lfs push가 먼저 이루어진다.(git lfs를 이용하는 과정에서 .gitattributes가 자동으로 생성됨)
```



* 좀 더 modern한 방법이라는 의견

```bash
Since Git LFS 2.2.0, git lfs migrat을 사용할 수 있다.
git lfs migrate import --include="[File Name]"
git lfs migrate import --include="*.확장자"
```

