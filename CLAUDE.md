# CLAUDE.md

Jekyll 기반 이력서 사이트. `sproogen/resume-theme` 원격 테마를 사용하며 레이아웃과 스타일을 로컬에서 오버라이드한다. 실제 배포 사이트: https://toongri.github.io/oh-my-resume/ — 콘텐츠 구조 상세는 `docs/config-guide.md` 참조.

이 프로젝트의 resume는 `_config.yml`이다.

## 개발 명령어

```bash
# Docker로 개발 서버 실행 (권장)
docker compose up
# → http://localhost:4000

# 로컬 Ruby 환경
bundle install
bundle exec jekyll serve --livereload
```

```bash
# PDF 생성
bun run pdf                   # main 브랜치 기준 PDF 생성
bun run pdf feature-branch    # 특정 브랜치 기준 PDF 생성
bun test                      # 테스트 실행
```

## 렌더링 흐름

`index.md` → `_layouts/default.html` → `_config.yml`의 `content` 배열을 순회하며 각 섹션을 렌더링.

- `section.title == "문제 해결"` → `section-projects.html`
- `section.layout == "text"` → `section-text.html`
- 그 외 → `section-list.html`

## 스타일 오버라이드

`_sass/modern-resume-theme.scss`가 엔트리포인트로, base/button/type/dark/icons를 임포트하고 커스텀 스타일을 추가한다.
