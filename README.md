# Gemini Enterprise 핸즈온 — GitHub Pages

워크샵 청중이 **프롬프트를 복사·붙여넣기** 하며 따라올 수 있는 단일 페이지입니다.

```
ge-workshop-handson/
├─ index.html     # 복사 버튼·목차·탭·모바일 대응 (md를 렌더링)
├─ handson.md     # 청중 핸즈온 (기본 페이지)
├─ console.md     # 호스트 구축 가이드 A~E
├─ .nojekyll      # Jekyll 처리 비활성화
└─ README.md
```

**두 페이지**를 하나의 `index.html`이 제공합니다 (상단 탭으로 전환):
- 청중 핸즈온 → `https://<USER>.github.io/ge-workshop/`
- 호스트 구축(A~E) → `https://<USER>.github.io/ge-workshop/?d=console`

수정은 **`handson.md` / `console.md`만** 편집하면 됩니다. `index.html`이 자동 렌더링하고 모든 코드 블록에 **복사** 버튼을 붙입니다.

> ℹ️ `console.md`는 호스트용 setup 가이드(`ge-workshop-setup/CONSOLE_STEPS.md`)의 사본입니다. 공개 Pages에 올리면 누구나 볼 수 있으니, 호스트 전용으로 두려면 별도 비공개 저장소를 쓰거나 `console.md`를 빼세요(청중 페이지만 공개).

## GitHub Pages 배포 (5분)

1. GitHub에 **공개(public) 저장소** 생성 (예: `ge-workshop`).
2. 이 폴더의 4개 파일을 저장소 루트에 push:
   ```bash
   cd ge-workshop-handson
   git init && git add . && git commit -m "handson page"
   git branch -M main
   git remote add origin https://github.com/<USER>/ge-workshop.git
   git push -u origin main
   ```
3. 저장소 **Settings → Pages** → *Build and deployment* → Source: **Deploy from a branch** → Branch: **main / (root)** → Save.
4. 1~2분 후 발행 URL 확인:
   ```
   https://<USER>.github.io/ge-workshop/
   ```
5. 이 URL을 워크샵 당일 채팅창/슬라이드로 공유하세요. (짧게 만들려면 `bit.ly` 등 단축 URL 사용)

> ⚠️ `index.html`은 `handson.md`를 `fetch`로 불러오므로 **웹 서버(=GitHub Pages)** 에서 열어야 합니다. 로컬 파일(`file://`)로 직접 열면 보안 정책상 안 됩니다.

## 로컬 미리보기
```bash
cd ge-workshop-handson
python3 -m http.server 8000
# 브라우저에서 http://localhost:8000
```

## 커스터마이징
- **내용**: `handson.md` 편집 (프롬프트는 ```` ``` ```` 코드 블록 안에 두면 복사 버튼이 붙음)
- **색/폰트**: `index.html` 상단 `<style>`의 `:root` 변수 (발표자료 팔레트와 동일: 네이비 `#0B2447`, 라이트블루 `#A5D7E8`)
- **제목/날짜**: `index.html`의 `<header class="top">`
