# Git flow

Git을 이용한 flow



![git flow](https://nvie.com/img/git-model@2x.png)



* **master branch** : 실제 앱 단계
* **develop branch** : 개발 단계

* **feature branch** : 세부적 개발 단계

master branch에서는 실제 앱에 구현되는 것을 결정한다.

개발을 위해 develop branch에서 작업이 수행되고 구현이 성공적으로 되었는지 여부는 develop branch에서 확인한다.

개발환경에서 협업을 위해 develop branch를 큰 줄기로 삼고 개발이 필요한 특정 부분들을 feature branch로 떼어내서 작업한다. 작업이 끝난 부분을 다시 develop branch로 가져와서 전체적인 개발을 완성한다.

feature branch에서 로그인 화면, 게시판 등의 기능 부분을 떼어내서 작업하고, 작업이 끝나면 제대로 구현되었는지 확인하여 develop branch로 규합된다. 이후 develop branch에서 선택되어 실제 앱 단계인 master branch로 적용된다.









