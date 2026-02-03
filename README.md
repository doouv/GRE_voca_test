# GRE Vocabulary Practice

GRE 단어 시험 연습 사이트 (GitHub Pages용)

## 🚀 빠른 시작

### 1. GitHub에 저장소 만들기
1. GitHub에서 새 저장소 생성 (예: `gre-vocab-practice`)
2. 이 폴더의 모든 파일을 업로드

### 2. GitHub Pages 활성화
1. 저장소 Settings → Pages
2. Source: `main` 브랜치, `/ (root)` 선택
3. Save 클릭
4. 몇 분 후 `https://[username].github.io/gre-vocab-practice/` 접속 가능

## 📁 파일 구조

```
gre-vocab-practice/
├── index.html          # 메인 페이지 (Word List 선택)
├── test.html           # 시험 페이지 (동적 JSON 로딩)
├── data/
│   ├── wordlist1.json  # Word List 1 데이터
│   ├── wordlist28.json # Word List 28 데이터
│   └── ...             # 추가 Word List
└── README.md
```

## 📝 새 Word List 추가하기

### 1. JSON 파일 형식

`data/wordlist{N}.json` 파일 생성:

```json
[
  {
    "qid": "q001",
    "word": "languid",
    "pos": "adj.",
    "meanings": ["나른한", "활기 없는"],
    "correct": ["A", "C"],
    "options": { "A": "listless", "B": "energetic", "C": "lethargic", "D": "vigorous" }
  },
  {
    "qid": "q002",
    "word": "ubiquitous",
    "pos": "adj.",
    "meanings": ["어디에나 있는"],
    "correct": ["B"],
    "options": { "A": "rare", "B": "omnipresent", "C": "scarce", "D": "uncommon" }
  }
]
```

### 2. 동의어 문제가 없는 단어 (뜻만)

```json
{
  "qid": "q003",
  "word": "serendipity",
  "pos": "n.",
  "meanings": ["우연한 행운", "뜻밖의 발견"],
  "correct": [],
  "options": {}
}
```
→ `options`가 비어있으면 동의어 문제 없이 뜻만 나옴

### 3. index.html에서 활성화

`index.html`의 JavaScript에서 `AVAILABLE_WORDLISTS` 배열 수정:

```javascript
const AVAILABLE_WORDLISTS = [1, 28, 29, 30]; // 추가한 번호 포함
```

## 📱 모바일 지원

- ✅ 터치 영역 최소 44px 확보
- ✅ backdrop-filter 버그 수정 (iOS Safari)
- ✅ 반응형 레이아웃
- ✅ 자동 저장 (localStorage)

## ✨ 기능

- **자동 저장**: 답안 작성 시 자동 저장
- **채점**: 정답 확인 및 점수 계산
- **Export**: JSON 파일로 답안 내보내기
- **진행 상황 추적**: 완료/진행 중 상태 표시
- **하이라이트**: 모르는 단어 표시 기능

## 🔧 커스터마이징

### Word List 총 개수 변경
`index.html`에서:
```javascript
const TOTAL_WORDLISTS = 30; // 원하는 개수로 변경
```

### 스타일 변경
각 HTML 파일의 `<style>` 섹션에서 CSS 변수 수정:
```css
:root {
  --green: #16A34A;  /* 정답 색상 */
  --red: #DC2626;    /* 오답 색상 */
  /* ... */
}
```

## 📄 라이선스

자유롭게 사용하세요!
