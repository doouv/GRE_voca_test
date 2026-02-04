# GRE Vocabulary Practice

그냥 빠르게 만든 단어 시험지... (GRE 이진세 선생님 단어장)

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
├── index.html              # 메인 페이지 (Word List 선택)
├── test.html               # 시험 페이지 (동적 JSON 로딩)
├── data/
│   ├── GRE_wordlist28.json # Word List 28 데이터
│   ├── GRE_wordlist29.json # Word List 29 데이터
│   ├── GRE_wordlist30.json # Word List 30 데이터
│   └── ...                 # 최대 50개까지 추가 가능
└── README.md
```

## 📝 새 Word List 추가하기

### 1. JSON 파일 형식

`data/GRE_wordlist{N}.json` 파일 생성 (N은 1-50 사이):

```json
[
  {
    "id": "001",
    "word": "languid",
    "pos": "adj.",
    "head_meanings": ["나른한", "활기 없는"],
    "synonyms_from_image": ["listless", "lethargic", "sluggish"]
  },
  {
    "id": "002",
    "word": "ubiquitous",
    "pos": "adj.",
    "head_meanings": ["어디에나 있는"],
    "synonyms_from_image": ["omnipresent", "pervasive"]
  }
]
```

**필드 설명:**
- `id`: 3자리 숫자 (예: "001", "002")
- `word`: GRE 단어
- `pos`: 품사 (n., v., adj., adv. 등)
- `head_meanings`: 단어의 뜻 (배열)
- `synonyms_from_image`: 동의어 목록 (배열) - 모두 정답으로 처리됨

### 2. 동의어가 없는 단어 (뜻만 표시)

```json
{
  "id": "003",
  "word": "serendipity",
  "pos": "n.",
  "head_meanings": ["우연한 행운", "뜻밖의 발견"],
  "synonyms_from_image": []
}
```
→ `synonyms_from_image`가 빈 배열이면 동의어 문제 없이 뜻만 표시됨

### 3. index.html에서 활성화

새 Word List를 추가한 후, `index.html`의 JavaScript에서 `AVAILABLE_WORDLISTS` 배열을 수정하세요:

```javascript
const AVAILABLE_WORDLISTS = [1, 50]; // 현재: 1번과 50번 사용 가능
// 또는 범위로 지정하려면 직접 배열 생성:
// const AVAILABLE_WORDLISTS = Array.from({length: 50}, (_, i) => i + 1); // 1-50 전체
```

**참고:** 현재 프로젝트에는 Word List 28-33이 포함되어 있습니다.

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
const TOTAL_WORDLISTS = 50; // 최대 50개까지 표시 (현재 설정)
// 더 많이 표시하려면 이 숫자를 늘리세요
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
