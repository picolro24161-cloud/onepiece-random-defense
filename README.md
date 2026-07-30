# 원피스 랜덤 디펜스

브라우저에서 동작하는 타워 디펜스 게임. 단일 `index.html` + 외부 에셋 구조.

## 구조

```
index.html          게임 본체 (약 460 KB, 로직 전체 인라인)
netlify.toml        Netlify 빌드/캐시 설정
_headers            캐시 헤더 (netlify.toml 백업용)
assets/
  img/    221개     캐릭터 스프라이트 · 보스 연출 이미지
  video/    9개     인트로 / 보스 / 클리어 연출
  audio/   10개     캐릭터 TTS
```

## 배포

빌드 과정이 없는 정적 사이트입니다. 저장소 루트가 그대로 사이트 루트입니다.

- **Build command**: 비움
- **Publish directory**: `.`

`assets/` 파일명은 내용 해시라서 내용이 바뀌면 파일명도 바뀝니다.
그래서 `netlify.toml` 에서 1년 `immutable` 캐시를 걸어도 안전합니다.

## 로컬 실행

`file://` 로 열어도 동작하지만, HTTP 로 서빙하는 편이 실제 배포 환경과 같습니다.

```bash
python3 -m http.server 8000
```

## 참고

- 게임 시작 전 이미지 221장을 전부 프리로드하고 진행률을 표시합니다.
- 카카오톡·인스타그램 등 인앱 브라우저는 감지해서 외부 브라우저로 열도록 안내합니다.
