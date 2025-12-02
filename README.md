# 미니 SNS 반응 시스템 - useState 마스터 클래스

useState만으로 1시간 동안 단계별 난이도 상승형 실습을 진행하는 프로젝트입니다.

## 📋 수업 목표

1시간 동안 useState의 모든 개념을 완전히 이해하고, 실제로 작동하는 미니 SNS 페이지를 완성하기

---

## 🚀 시작하기

### 1단계: 프로젝트 클론 및 설치

```bash
# 템플릿 프로젝트 클론
git clone https://github.com/sum37/ksop_8th.git
cd ksop_8th

# 의존성 설치
npm install

# 개발 서버 실행
npm run dev
```

브라우저에서 `http://localhost:5173`으로 접속하여 확인할 수 있습니다.

---

## 📚 수업 구성 (정확히 1시간)

### 1️⃣ [0-10분] useState 개념 + 기본 Counter 실습

**목표:**
- state가 왜 필요한지 이해
- UI가 다시 렌더링되는 경험 제공

**핵심 코드:**
```tsx
const [count, setCount] = useState(0);

<button onClick={() => setCount(count + 1)}>+</button>
<h1>{count}</h1>
```

**학생 활동:**
- 버튼을 클릭하면 숫자가 증가하는 것을 확인
- 리셋 버튼으로 0으로 돌아가는 것 확인
- "state가 바뀌면 화면이 자동으로 업데이트된다" 체감

---

### 2️⃣ [10-25분] 좋아요 버튼 만들기

**목표:**
- boolean 상태 토글
- 조건부 렌더링 (색/아이콘 변경)

**핵심 코드:**
```tsx
const [liked, setLiked] = useState(false);

<button onClick={() => setLiked(!liked)}>
  {liked ? "❤️ 좋아요" : "🤍 좋아요"}
</button>
```

**학생 활동:**
- 좋아요 버튼 클릭 시 아이콘과 색상이 바뀌는 것 확인
- Tailwind를 사용하여 색상 변경 효과 체험
- boolean 상태의 토글 개념 이해

---

### 3️⃣ [25-40분] 한 줄 댓글 시스템 만들기

**목표:**
- input 상태 관리
- 리스트 상태 관리
- 배열에 push하는 대신 새로운 배열 만들기 (`setPosts([...posts, newPost])` 패턴)

**핵심 코드:**
```tsx
const [text, setText] = useState("");
const [posts, setPosts] = useState([]);

<input 
  value={text} 
  onChange={(e) => setText(e.target.value)} 
/>

<button onClick={() => {
  setPosts([...posts, text]);
  setText("");
}}>
  등록하기
</button>

<ul>
  {posts.map((p, i) => <li key={i}>{p}</li>)}
</ul>
```

**학생 활동:**
- 입력창에 텍스트를 입력하고 등록 버튼 클릭
- 입력한 값이 바로 UI에 반영되는 경험
- 배열에 새로운 항목을 추가하는 방법 이해
- `...posts` (스프레드 연산자) 개념 이해

---

### 4️⃣ [40-55분] 다크모드 토글 만들기

**목표:**
- 전역 테마처럼 보이지만 사실은 단순 useState
- className 조건부 변경

**핵심 코드:**
```tsx
const [dark, setDark] = useState(false);

<div className={dark ? "bg-black text-white" : "bg-white text-black"}>
  <button onClick={() => setDark(!dark)}>
    {dark ? "라이트 모드" : "다크 모드"}
  </button>
</div>
```

**학생 활동:**
- 다크모드 버튼 클릭 시 전체 페이지 테마 변경 확인
- 조건부 className 적용 방법 이해
- useState로 전역적인 효과를 낼 수 있다는 것 체감

---

### 5️⃣ [55-60분] 최종 통합

**목표:**
- 좋아요 버튼, 댓글 리스트, 다크모드를 하나의 페이지에 통합
- "미니 SNS 페이지" 완성

**학생 활동:**
- 모든 기능이 하나의 페이지에서 작동하는 것 확인
- useState만으로 이렇게 멋진 인터랙티브 웹페이지를 만들 수 있다는 성취감
- Git push까지 완성

---

## 📁 프로젝트 구조

```
ksop_8th/
├── src/
│   ├── App.tsx              # 모든 실습이 통합된 메인 컴포넌트
│   ├── main.tsx             # React 진입점
│   └── index.css            # Tailwind CSS 설정
├── index.html
├── tailwind.config.js
├── package.json
└── README.md
```

---

## 💾 Git으로 저장소에 올리기

### 1단계: 변경사항 확인

```bash
git status
```

### 2단계: 변경사항 추가

```bash
git add .
```

### 3단계: 커밋 메시지 작성

```bash
git commit -m "useState 실습 완성"
```

### 4단계: 자신의 GitHub 저장소에 올리기

**⚠️ 중요: 원본 템플릿 저장소에 push하지 않도록 주의하세요!**

```bash
# 원본 remote 제거 (중요!)
git remote remove origin

# 자신의 GitHub 저장소 추가
git remote add origin https://github.com/본인아이디/본인저장소이름.git

# 브랜치 이름을 main으로 설정
git branch -M main

# GitHub에 push
git push -u origin main
```

---

## 🎯 useState 핵심 정리

### useState 기본 문법

```tsx
const [상태변수, 상태변경함수] = useState(초기값);
```

### useState의 3가지 사용 패턴

1. **숫자 상태**
   ```tsx
   const [count, setCount] = useState(0);
   setCount(count + 1);
   ```

2. **boolean 상태**
   ```tsx
   const [liked, setLiked] = useState(false);
   setLiked(!liked); // 토글
   ```

3. **배열 상태**
   ```tsx
   const [posts, setPosts] = useState([]);
   setPosts([...posts, newPost]); // 새로운 배열 만들기
   ```

### 중요한 규칙

- **절대 직접 수정하지 않기!**
  - ❌ `posts.push(newPost)` (잘못된 방법)
  - ✅ `setPosts([...posts, newPost])` (올바른 방법)

- **state가 바뀌면 컴포넌트가 다시 렌더링됩니다!**
  - 이것이 React의 핵심입니다!

---

## 🛠️ 기술 스택

- React 19
- TypeScript
- Vite
- Tailwind CSS 3

---

## 📝 수업 진행 팁

1. **각 실습마다 5분씩 여유 시간을 두세요**
   - 학생들이 코드를 직접 타이핑하고 실험할 시간이 필요합니다

2. **"왜 이렇게 해야 하나요?" 질문에 대비하세요**
   - 배열을 직접 수정하지 않는 이유
   - state가 바뀌면 자동으로 렌더링되는 이유

3. **학생들이 직접 값을 바꿔보게 하세요**
   - 숫자를 바꿔보기
   - 색상을 바꿔보기
   - 텍스트를 바꿔보기

4. **최종 통합 시간에 성취감을 느끼게 하세요**
   - "우리가 이걸 만들었어요!" 느낌을 주세요

---

## 🎉 완성 화면 구성

```
┌─────────────────────────────────┐
│  미니 SNS 반응 시스템            │
├─────────────────────────────────┤
│  [Counter: - 0 +]               │
├─────────────────────────────────┤
│  [❤️/🤍 좋아요 버튼]            │
├─────────────────────────────────┤
│  [댓글 입력창] [등록하기]        │
│  💬 댓글 1                       │
│  💬 댓글 2                       │
├─────────────────────────────────┤
│  [🌙 다크모드 토글]              │
└─────────────────────────────────┘
```

---

**useState 마스터가 되기를 응원합니다! 🚀**


# ksop_8th
