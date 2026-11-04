# 고정 QR 동영상 호스팅

QR 코드는 **한 번만 인쇄**하고, 보여줄 동영상은 **`video.json` 만 수정**해서 언제든 바꿉니다.

```
QR (고정) ──► https://jungpyo76.github.io/special/ ──► video.json 에 적힌 영상 재생
```

## 1. 최초 1회 설정 (GitHub Pages 켜기)

1. GitHub 저장소 → **Settings → Pages**
2. *Source*: `Deploy from a branch`, *Branch*: `main` / `/ (root)` → **Save**
3. 1~2분 뒤 `https://jungpyo76.github.io/special/` 접속 확인
4. `qr.png` 를 인쇄/배포 (이 QR은 앞으로 바꿀 필요 없음)

> 이 작업 브랜치(`claude/fixed-qr-video-hosting-e54am7`)를 `main` 에 병합한 뒤 Pages를 켜세요.
> 저장소가 private 이면 GitHub Pages는 유료 플랜에서만 됩니다 → public 으로 두세요.

## 2. 동영상 바꾸기 (매번)

GitHub 웹에서 `video.json` 열기 → 연필(✏️) 아이콘 → 수정 → **Commit changes**

```json
{
  "title": "오늘의 영상",
  "url": "https://www.youtube.com/watch?v=영상ID"
}
```

`url` 에 넣을 수 있는 것:

| 종류 | 예시 | 비고 |
|---|---|---|
| YouTube (일부공개 가능) | `https://youtu.be/xxxxxxxxxxx` | 가장 추천. 용량 제한 없음 |
| Google Drive | `https://drive.google.com/file/d/파일ID/view` | 공유 설정을 "링크가 있는 모든 사용자" 로 |
| Vimeo | `https://vimeo.com/123456` | |
| 저장소 안의 파일 | `videos/clip.mp4` | `videos/` 폴더에 업로드. 파일당 100MB 미만(웹 업로드는 25MB) |

커밋 후 반영까지 보통 1분 내외(최대 약 10분)입니다. QR을 다시 찍으면 새 영상이 나옵니다.

## 파일 구성

- `index.html` — QR이 가리키는 플레이어 페이지 (수정 불필요)
- `video.json` — **지금 보여줄 영상** (이것만 수정)
- `qr.png` — 고정 QR 코드 (`https://jungpyo76.github.io/special/`)
- `videos/` — 직접 올리는 영상 파일 보관용 (선택)
