---
title: minimal-mistakes 테마를 이용한 GitHub 블로그 생성
categories:
  - Blogs
tags:
  - Blog
  - minimal-mistakes
---

> ## 서론
Github Pages상에 Jekyll 기반의 블로그 사이트 구축

> ## 준비작업
- Github Pages 상에서 블로그 호스팅을 위해서는 특별한 이름의 repository가 필요
- `#{GITHUB_ID}.github.io` 라는 이름으로 리파지토리를 생성

> ## 테마 가져오기

> 아래 내용은 [minimal-misatakes의 퀵가이드](https://mmistakes.github.io/minimal-mistakes/docs/quick-start-guide/) 를 참조 및 요약한 글.

[minimal-mistakes](https://github.com/mmistakes/minimal-mistakes) 에서 Fork 또는 downlaod 및 업로드를 통하여 소스를 카피. 소스 카피 시 옮기기 전에 쓸데없는 것은 삭제. 삭제해야 할 리스트는 아래와 같다.
- `.editorconfig`
- `.gitattributes`
- `.github`
- `/docs`
- `/test`
- `CHANGELOG.md`
- `minimal-mistakes-jekyll.gemspec`
- `README.md`
- `screenshot-layouts.png`
- `screenshot.png`

`Gemfile`을 아래 코드로 대체한다.
```ruby
source "https://rubygems.org"

gem "github-pages", group: :jekyll_plugins

group :jekyll_plugins do
  gem "jekyll-paginate"
  gem "jekyll-sitemap"
  gem "jekyll-gist"
  gem "jekyll-feed"
  gem "jemoji"
end
```
Gem을 통해 `bundler` 를 설치하자. 이제 Jekyll 명령어를 `bundle exec jekyll build` 와 같이 실행 할 수 있다. 로컬에서 확인을 위해서 `bundle exec jekyll serve` 명령어를 사용하면 된다.

> ## 포스트 쓰기
포스트는 특정 제목으로 작성되어야 한다. `YYYY-MM-DD-{TITLE}.md` 로 작성하면 된다.
내용은 크게 두 부분으로 나눌 수 있다. 메타데이터를 위한 yaml 부분과 본문을 위한 마크다운 부분이다. yaml은 md 파일의 머릿말에 적으면 된다. 아래가 그 예제이다.
```yaml
---
title: Jekyll과 minimal-mistakes 테마를 이용한 블로그 생성
categories:
  - Life
tags:
  - life
---
```

> ## 카테고리, 태그 적용
`minimal-mistakes`카테고리와 태그를 지원은 하지만 기본 설정되어 있지는 않다. `minimal-mistakes`의 [깃헙 페이지의 docs 폴더](https://github.com/mmistakes/minimal-mistakes/tree/master/docs) 를 참고하면 다양한 예제들을 가져올 수 있다. 해당 예제들은 [데모](https://mmistakes.github.io/minimal-mistakes/)로 제공되는 페이지의 코드들이다. 이 폴더의 `_pages` 하위 폴더의 `category-archive.html`와 `tag-archive.html`을 그대로 가져와서 `_pages`를 만들고 옮겨놓으면 된다.

