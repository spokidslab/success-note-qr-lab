# SUCCESS NOTE | QR LAB V2

SPOKIDS LAB의 GAME REVIEW 노트용 YouTube 장면별 QR 생성 웹앱입니다.

## 시간 입력

각 장면에 영상 **시작·종료 시점 모두 필수**이며, 두 값 모두 YouTube 영상 타임라인 기준입니다. 스코어보드 시간은 별도로 입력합니다.

## 실행

```bash
npm install
npm run dev
```

## 공개 배포 (Cloudflare Pages 추천)

1. 이 폴더를 GitHub 저장소에 업로드합니다.
2. Cloudflare Dashboard → Workers & Pages → Create → Pages → Connect to Git에서 저장소를 선택합니다.
3. Framework preset: `Vite` (또는 None), Build command: `npm run build`, Build output directory: `dist`.
4. 배포 후 제공되는 `*.pages.dev` 주소를 테스트합니다.
5. 추후 소유 도메인이 있으면 Pages의 Custom domains에서 연결합니다.

대안: Netlify에서 Git 저장소 연결 → Build command `npm run build`, Publish directory `dist`.

## 작동 및 개인정보

- 영상 ID, 시간, QR은 사용자의 브라우저에서 처리하며 별도 애플리케이션 DB로 전송하지 않습니다. 외부 YouTube 방문 시 해당 서비스의 정책이 적용됩니다. 백엔드/DB/로그인 없음.
- YouTube 시청 권한은 원본 영상 설정에 따릅니다.
- QR은 영상의 **시작 시점**으로 연결됩니다. 종료 시점은 별도의 **구간 재생 시험** 링크(YouTube embed start/end)에 사용합니다. 단, QR 자체는 호환성을 위해 시작 시점 링크로 연결됩니다. YouTube 플레이어 환경에 따라 구간 재생 동작이 달라질 수 있습니다.
- 입력 데이터는 저장하지 않으므로 새로고침하면 사라집니다.
- PNG는 개별 저장 가능. 여러 PNG의 일괄 다운로드는 브라우저의 다중 다운로드 허용 설정에 따라 차단될 수 있습니다.
- A4 인쇄는 30×30mm QR을 5열로 배치합니다. 인쇄 설정 배율 100%, 머리글/바닥글 끄기. 실제 라벨지 제조사의 상하좌우 여백과 칸 간격은 다를 수 있으므로 일반 A4 시험 인쇄 후 조정이 필요합니다.

## 다음 개선 항목

- 실제 구매한 라벨지 제조사 규격에 맞춘 템플릿 (행/열 간격, 시작 여백)
- 장면 CSV 가져오기/내보내기
- 모바일 사용성 테스트 및 QR 스캔 실물 검증
- 커스텀 도메인 및 브랜드 정책 페이지
