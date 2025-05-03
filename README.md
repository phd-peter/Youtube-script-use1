# YouTube Thread & LinkedIn Post Generator

---

## ⚠️ 클론 후 필수 초기 설정 안내

- 이 저장소에는 보안 및 빌드 산출물 관련 파일이 포함되어 있지 않습니다.
- 아래 파일/폴더는 `.gitignore`에 의해 깃허브에 올라가지 않습니다:
  - 환경 변수 파일: `.env.local` 등 `.env*` 파일
  - 빌드/캐시 폴더: `.next/`, `node_modules/`, `/out/`, `/build/` 등
  - 기타: `.DS_Store`, 로그 파일 등

**따라서, 저장소를 클론한 후 반드시 아래 작업을 진행하세요:**

1. **환경 변수 파일 생성**
   - 프로젝트 루트에 `.env.local` 파일을 만들고 아래와 같이 입력:
     ```
     GEMINI_API_KEY=your_google_gemini_api_key
     ```
   - (API Key는 [Google AI Studio](https://aistudio.google.com/app/apikey) 등에서 발급)

2. **의존성 설치 및 개발 서버 실행**
   ```bash
   pnpm install
   pnpm dev
   ```

3. **빌드 폴더(.next 등)는 자동 생성되므로 신경쓰지 않아도 됩니다.**

---

## 주요 기능

- 유튜브 링크 입력 → 영상 임베딩, 자막 추출
- Gemini AI로 LinkedIn 스레드/게시글 자동 생성
- 스레드는 `---SPLIT---` 구분자로 분리, 각 항목별/전체 복사 버튼 제공
- TailwindCSS 기반 반응형 UI, 접근성 고려
- 모든 에러는 명확한 메시지로 안내

## 사용법

1. 유튜브 링크 입력 후 **제출**
2. 자막 확인 및 **스레드/링크드인 게시글 생성** 클릭
3. 각 결과 옆 **복사** 버튼으로 손쉽게 복사 (복사 시 "복사됨" 안내)

## 환경 변수 설정

- `.env.local` 파일에 아래와 같이 추가:
  ```
  GEMINI_API_KEY=your_google_gemini_api_key
  ```

## 폴더 구조

- `app/page.tsx` : 메인 UI, 입력창, 결과 표시, 복사 기능 등
- `app/actions/youtube.ts` : 서버 액션(자막 추출, Gemini API 호출)
- `app/api/youtube-script/route.ts` : API 라우트, 액션 호출 및 응답 처리

## 기술 스택

- Next.js 15, React 19, TypeScript
- Tailwind CSS (UI 스타일링)
- LangChain (유튜브 자막 추출)
- @google/generative-ai (Gemini API)
- pnpm (패키지 매니저, pnpm-lock.yaml만 유지)

## 개발/운영 안내

- **pnpm만 사용**: `pnpm install`, `pnpm dev`, `pnpm build`
- `package-lock.json`은 존재하지 않으며, `pnpm-lock.yaml`만 유지됩니다.
- 팀원 및 CI 환경에서도 pnpm 사용 필수
- pnpm이 없다면 [공식 설치 가이드](https://pnpm.io/installation) 참고

## 기여 및 확장

- 새로운 기능 추가/확장 시 my-rule(원소스 멀티유즈 구조 및 규칙) 우선 준수
- UI/UX는 tailwindcss 기반, 반응형/가독성/접근성 고려
- 에러는 명확한 메시지로 안내

---

## Getting Started

```bash
pnpm install
pnpm dev
```

Open [http://localhost:3000](http://localhost:3000) with your browser to see the result.

You can start editing the page by modifying `app/page.tsx`. The page auto-updates as you edit the file.

This project uses [`next/font`](https://nextjs.org/docs/app/building-your-application/optimizing/fonts) to automatically optimize and load [Geist](https://vercel.com/font), a new font family for Vercel.

<details>
<summary>npm/yarn/bun 명령어도 참고용으로 남깁니다 (공식 지원은 pnpm만)</summary>

```bash
npm run dev
# or
yarn dev
# or
bun dev
```

</details>

## Learn More

To learn more about Next.js, take a look at the following resources:

- [Next.js Documentation](https://nextjs.org/docs) - learn about Next.js features and API.
- [Learn Next.js](https://nextjs.org/learn) - an interactive Next.js tutorial.

You can check out [the Next.js GitHub repository](https://github.com/vercel/next.js) - your feedback and contributions are welcome!

## Deploy on Vercel

The easiest way to deploy your Next.js app is to use the [Vercel Platform](https://vercel.com/new?utm_medium=default-template&filter=next.js&utm_source=create-next-app&utm_campaign=create-next-app-readme) from the creators of Next.js.

Check out our [Next.js deployment documentation](https://nextjs.org/docs/app/building-your-application/deploying) for more details.
