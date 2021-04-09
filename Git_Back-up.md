# Back-up

Local Repository1 ==backup==> Remote Repository

remote repository	==clone==> Local Repository2

Local Repository2	 ==push==> Remote Repository

Local Repository1 <==pull== Remote Repository



|                          | Local => Remote | Remote => Local |
| ------------------------ | --------------- | --------------- |
| HTTP(보안 하, 학습량 하) |                 |                 |
| SSH(보안 고, 학습량 고)  |                 |                 |



### 1. `git log`

commit 목록(log) 출력

* `git log --ineline` : 한줄씩 출력
* `git log -1` : 출력 개수 한정 (-2, -3 등)



### 2. `git restore [파일명]`

최종 커밋 시점으로 파일 상태를 복원 (restore)

* 커밋 이전, stage에 add된 상태(tracked)에서 주로 사용

* `git restore --staged [파일명] ` 



### 3. `git diff [파일명]`

변경 내역 출력



### 4. `git remote`

원격 저장소 정보 출력

* `git remote -v` : 상세 출력 (verbose의 약자)
* `git remote add [이름] [주소]` : 원격 저장소 정보 추가
  * 이름: 관례/관습적(Convention)으로 **origin** (원본) 
  * 주소: Github에서 복사 가능



### 5. `git push [이름] [브랜치]`

원격 저장소에 업로드

* `git push origin master` : Github에 업로드

```
Enumerating objects: 8, donw.
Counting objects: 100% (8/8), done.
Delta compression using up to 12 threads
Compressing objects: 100% (4/4), done.
Writing objects: 100% (8/8), 668 bytes | 668.00 kiB/s, done.
Total 8 (delta 0), reused 0 (delta 0), pack-reused 0
To heeps://github.com/hphk-john/git_review.git
 * [new branch]		master -> master
```



* `git push --set-upstream origin master` : origin master를 기본으로 설정
  * 설정 이후에는 git push만 해도 됨.

* `git pull origin master` : 내용물 받아오기



### 6. `git clone [저장소주소]`

저장소 복제

>  ex) `git clone https://github.com/git/git.git` : github의 git저장소 복제

















