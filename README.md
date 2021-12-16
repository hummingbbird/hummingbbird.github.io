###blog 작성과정
1.Git 설치 및 연결 작업
다음 명령어를 순서대로 실행합니다.
1.Git 설치 
sudo apt-get install git
sudo apt install git
git --version 을 입력해 잘 설치되었는지 확인합니다.

2.로컬 저장소 연결
git config --global user.name [깃허브 닉네임]
git config --global user.mail [깃허브와 연결된 내 메일 주소]


+)깃 간단한 명령어
1.git add : 수정한 코드 선택
2.git commit -m "comment" : 커밋하기
3.git push : 로컬 저장소에서 원격 저장소 업데이트
4.git pull : 원격 저장소에서 로컬 저장소 업데이트
->앞으로 대부분의 작업 후 1,2,3 세가지의 과정을 필수적으로 거쳐야 합니다.

2.깃허브 페이지 만들기
1.깃허브에서 [username].github.io 라는 이름을 가진 repository를 생성합니다.
2.생성된 repository의 url을 복사합니다.
3.git clone [나의 깃허브 url] 하여 로컬 저장소의 repository와 연동합니다.
4.'index.html'이라는 이름의 예시 파일을 작성합니다(blog_two문서 참조)
5.앞서 말한대로 1, 2번의 과정을 거칩니다.
6.3번 과정을 거치기 전 필요한 token을 가져와야합니다.
나의 github 들어가기 Setting->Developer settings->Personal access tokens->Generate new token
생성이 완료된 토큰을 복사하여 비밀번호처럼 사용합니다.(단, 복사한 토큰은 잃어버리지 않게 잘 복사해두세요! 그렇지 않으면 다시 새 토큰을 만들어야 합니다.)
7.git push 과정에서 비밀번호 칸에 복사한 토큰을 입력해주면 성공입니다.
8.github->Repository Settings > Pages 로 들어가 중간에 있는 주소로 접속해주면 내가 만든 예시 파일 대로 잘 작성이 된 것을 확인할 수 있습니다.

3.지킬 설치하기
1.지킬을 설치하기 전 확인 작업을 거칩니다.
https://jekyllrb-ko.github.io/docs/installation/ubuntu/ 이 링크를 타고 들어가서 설명을 따라서 잘 실행을 해줍니다.
2.jekyll -v를 통해 지킬이 잘 설치되어 있는지 확인한 후, jekyll new .--force 를 통해 현재 디렉토리에 지킬을 설치해줍니다.
3.실행 후 ls 명령어를 입력해보면 많은 파일이 생겼음을 알 수 있습니다.
4.bundle exec jekyll serve 실행 후, localhost:4000에 접속해주어, 사이트가 잘 생성 되었음을 확인해줍니다.

4.포스트 업로드하기
1.YYYY-MM-DD-TITLE.md의 형태로 새로운 문서를 생성합니다.
2.
---
layout: post
title: "MongoDB 정리"
date: 2021-12-10 19:14:23 +0900
categories: jekyll update
---
위와 같은 형식으로 문서를 시작합니다.
3.markdown 형식을 통해 내용을 작성하고 1-1,2,3의 과정을 거칩니다.
4.다시 3-4번 과정을 통해 잘 연동이 되었는지 확인해줍니다.

5.테마 설치하기
1.http://jekyllthemes.org/ 사이트에 들어가 원하는 테마를 골라줍니다.
2.선택한 테마를 git clone 해서 로컬에 받아온 후, _posts 파일을 제외하고 모든 테마를 덮어씌워줍니다.
3.변경된 파일들을 git에 반영해주면 테마가 잘 적용되었음을 확인할 수 있습니다.

6.댓글 기능 구현하기
1.https://disqus.com/ 사이트에 들어가 회원가입을 진행합니다.
2.'I want to install Disqus on my site'를 선택합니다.
3.사이트 정보를 입력합니다.(이 때, Website Name을 잘 기억해둡니다.)
4.지킬 플랫폼을 선택한 후, Configure를 눌러 다음을 진행합니다.
5.Website URL에 이름과 url을 잘 입력한 후 Next 버튼을 누릅니다.
6.Comment 정책을 선택한 후 Complete Setup을 눌러 설정을 마무리해줍니다.
7._config.yml 파일의 #Custom vars 에 다음과 같은 key-value를 추가해줍니다.
comment:
  provider:		"disqus"
  disqus:
    shortname:		"website name"
8.disqus 홈페이지에서 Universal Code를 복사한 후 페이지에 맞게 수정을 해줍니다. 위 아래에 {% if.page.comments &} , {% endif %}를 입력해줍니다.
9._layouts/post.html 파일에서 let PAGE_URL과 PAGE_IDENTIFIER 부분을 수정해줍니다.
10.s.src에 아까 복사한 url을 입력해줍니다. 그리고 댓글을 허용하고 싶은 곳에 comments: true를 입력해주면 완성!(물론 당연히 2-1,2,3 과정을 거쳐야 합니다.)


