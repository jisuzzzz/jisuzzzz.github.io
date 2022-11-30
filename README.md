# Build-up
## start from git
1. github에서 username.github.io 으로 public repositories 생성
2. `$ git clone <repository link>`으로 public repositories clone
3. `$ git branch` -M main 으로 현재 branch를 main으로 변경
4. `$ git status` 으로 상태 확인 후 대기
---
## install Jekyll
Jekyll은 Ruby언어로 만들어져 있어 Ruby 설치가 필요하다.


Mac에는 기본적으로 Ruby가 설치되어있으나 오래된 버전이기에 Jekyll을 지원하지 않을 가능성이 높다


1. Command Line Tools 설치(Xcode가 있는 경우 패스)


`$ xcode-select —install`


2. Ruby 설치
2. 1. Homebrew 설치


`$ /bin/bash -c “$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"`


2. 2. rbenv(Ruby Version Manager)설치


`$ brew install rbenv`


2. 3 rbenv 설정


`$ echo ‘if which rbenv > /dev/null; then eval “$(rbenv init -)”;fi’ >>~/.bash_profile`


`$ source ~/.bash_profile`


2. 4. Ruby 다운로드


`$ rbenv install 3.1.0`



전역에서 사용할 Ruby 버전을 지정한다


`$ rbenv global 3.1.0`


다음 명령어로 올바르게 설치 되어있는지 체크


`$ rbenv versions`


`$ ruby -v`


3. Jekyll 설치


`$ gem install jekyll bundler github-pages`


## 테마 설치


1. 원하는 테마를 설치한 후 압축 해제한 파일을 jisuzzzz.github.io 폴더에 붙여넣기 동일한 파일들은 덮어씌우기
2. 테마에 필요한 패키지를 bundle install을 통해 설치
3. `$ bundle exec jekyll serve` 를 쳐서 블로그 실행
4. Lanyou 테마 적용 확인
5. _config.yml에서 원래 작성된 부분을 내 블로그에 맞춰서 수정


```
# Setup
title: Jisu's Blog
tagline: 'Until Die'
description: 'No Post Blog Made by <a href="https://instagram.com/zzzzsuzz"
target="_blank">@zzzzsuzz</a>.'
url: https://jisuzzzz.github.io/
baseurl: ''
paginate: 5
permalink: pretty
# About/contact
author:
name: Jisu Kim
url: https://instagram.com/zzzzsuzz
email: meked@naver.com
# Gems
plugins:
- jekyll-paginate
comment:
provider: "disqus"
disqus:
shortname: "jisu-comments"
analytics:

provider : "google-gtag" # false (default), "google", "google-universal", "google-gtag", "custom"
google:
tracking_id : "G-0LJTEH3T0N"
anonymize_ip : false
# Custom vars
version: 1.1.0
google_analytics_id: #UA-XXXX-Y
```


## 댓글 추가
1. Disqus 사이트에 접속해 가입
2. 가입 과정중 사이트 정보 입력할 때 Website Name 기억
3. Jekyll Platform 선택, Website URL에 깃블로그 주소 입력
4. _config.yml에 아래 코드 입력


```
comment:
provider: “disqius”
disqus:
shortname: “<Website Name>
```


5. _layouts/post.html에 아래 코드 입력


```
{% if page.comments %}
<div id="disqus_thread"></div>
<script>
/**
* RECOMMENDED CONFIGURATION VARIABLES: EDIT AND UNCOMMENT
* THE SECTION BELOW TO INSERT DYNAMIC VALUES FROM YOUR
* PLATFORM OR CMS.
*
* LEARN WHY DEFINING THESE VARIABLES IS IMPORTANT:
* https://disqus.com/admin/universalcode/#configuration-variables
*/
let PAGE_URL = "{{site.url}}{{page.url}}"
let PAGE_IDENTIFIER = "{{page.url}}"
var disqus_config = function () {
// Replace PAGE_URL with your page's canonical URL variable
this.page.url = PAGE_URL;
// Replace PAGE_IDENTIFIER with your page's unique identifier variable
this.page.identifier = PAGE_IDENTIFIER;
};
(function() { // REQUIRED CONFIGURATION VARIABLE: EDIT THE SHORTNAME BELOW
var d = document, s = d.createElement('script');
// IMPORTANT: Replace EXAMPLE with your forum shortname!
s.src = 'https://lee-super.disqus.com/embed.js'; // 이부분에 Website Name 입력해야함!
s.setAttribute('data-timestamp', +new Date());
(d.head || d.body).appendChild(s);
})();
</script>
<noscript>
Please enable JavaScript to view the
<a href="https://disqus.com/?ref_noscript" rel="nofollow">
comments powered by Disqus.
</a>
</noscript>
{% endif %}
```


6. 포스트 작성할 때 comments: True


## 파비콘 설정
1. /assets 폴더 내에 favicon.ico 파일을 넣어줌
2. _includes 폴더 내에 head.html의 위쪽에 아래 코드 삽입 `<link rel=“icon” type=“image/png” href=“/assets/favicon.ico”>`


Google Analytics에 대한 내용은 블로그에 포스팅
