# DialogVLA Project Page

SpatialVLA / Nerfies 스타일의 학술 프로젝트 홈페이지. `index.html` 하나로 동작하는 정적 페이지입니다.

## 폴더 구조
```
dialogvla-page/
├── index.html            # 페이지 전체 (여기만 수정하면 됨)
├── static/
│   ├── images/           # 논문 그림 (teaser.png, paradigms.png, architecture.png, two_stage.png)
│   └── videos/           # 데모/태스크 영상 (demo.mp4, handover.mp4 ...)
└── README.md
```

## 그림/영상 넣는 법
`index.html` 안에 `<div class="ph">...</div>` 로 된 placeholder 자리가 있습니다.
파일을 `static/images/` 에 넣고, 해당 placeholder를 아래처럼 교체하세요.

이미지:
```html
<img src="static/images/architecture.png" alt="DialogVLA architecture">
```

영상 (자동 재생 루프):
```html
<video autoplay muted loop playsinline>
  <source src="static/videos/demo.mp4" type="video/mp4">
</video>
```

## arXiv / Code 링크 활성화
지금은 Paper / arXiv / Code 버튼이 `class="btn disabled"` (Coming Soon) 상태입니다.
준비되면 해당 `<a>` 태그에서 `disabled` 만 지우고 `href` 를 채우면 됩니다.
```html
<!-- before -->
<a class="btn disabled" href="#" aria-disabled="true"> ... arXiv <span class="soon">SOON</span></a>
<!-- after -->
<a class="btn" href="https://arxiv.org/abs/XXXX.XXXXX"> ... arXiv</a>
```
`<span class="soon">SOON</span>` 도 같이 지워주세요.

## GitHub Pages 배포 (무료, spatialvla.github.io 와 같은 방식)
1. GitHub 새 repo 생성. 개인 사이트 주소를 쓰려면 repo 이름을 `dialogvla`(또는 아무거나)로 만들면 됩니다.
   - `USERNAME.github.io/dialogvla/` 로 배포됨
   - 만약 `USERNAME.github.io` 라는 이름으로 repo를 만들면 최상위 도메인이 됩니다.
2. 이 폴더 내용을 push:
   ```bash
   cd dialogvla-page
   git init
   git add .
   git commit -m "DialogVLA project page"
   git branch -M main
   git remote add origin https://github.com/USERNAME/dialogvla.git
   git push -u origin main
   ```
3. GitHub repo → **Settings → Pages** → Source를 `main` 브랜치 `/ (root)` 로 지정 → Save.
4. 1~2분 뒤 `https://USERNAME.github.io/dialogvla/` 접속.

## 로컬 미리보기
```bash
cd dialogvla-page
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000
```

## 커스터마이즈 팁
- 강조 색상: `index.html` 상단 `:root` 의 `--accent` (기본 파란색) 값을 바꾸면 전체 톤이 바뀝니다.
- 저자 링크: 지금 `href="#"` 로 되어 있는 저자 이름에 개인 홈페이지/구글스칼라 주소를 넣으세요.
- 소셜 미리보기(og:image): 배포 후 `static/images/teaser.png` 를 실제 파일로 채우면 카톡/트위터 공유 썸네일이 나옵니다.
