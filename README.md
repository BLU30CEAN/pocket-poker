# 🃏 Pocket Poker GTO - 지능형 포커 전략 분석기

직관적인 UI/UX로 누구나 쉽게 GTO(Game Theory Optimal) 전략을 학습할 수 있는 React Native 앱입니다.

## ✨ 주요 특징

### 🔍 실시간 지능형 검색
- 포지션, 핸드, 팟 사이즈 등을 입력하면 즉시 분석 결과 제공
- 300ms 디바운싱으로 부드러운 실시간 반응

### ℹ️ 직관적인 정보 시스템  
- 모든 검색 옵션 옆에 (i) 버튼
- 탭하면 상세 설명과 **학습 효과** 미리보기
- "이걸 배우면 뭐가 좋아지는지" 명확히 제시

### 📊 실시간 기대효과 미리보기
- 승률, 기댓값(EV), 추천 액션 즉시 계산
- 리스크 레벨과 신뢰도까지 표시
- 학습 포인트와 분석 근거 상세 제공

### 🎯 Progressive Disclosure
- 초보자: 간단한 색상과 즉석 답변
- 중급자: 상세한 분석과 근거
- 고급자: 복합적 시나리오 분석

## 🚀 시작하기

### 필요사항
- Node.js 18 이상
- Expo CLI
- iOS Simulator 또는 Android Emulator

### 설치 및 실행

```bash
# 의존성 설치
npm install

# 개발 서버 시작
npm start

# iOS에서 실행
npm run ios

# Android에서 실행  
npm run android

# 웹에서 실행
npm run web
```

## 🏗️ 프로젝트 구조

```
src/
├── components/          # 재사용 가능한 UI 컴포넌트
│   ├── SearchInput.tsx  # 스마트 검색 입력
│   ├── InfoModal.tsx    # 정보 모달 (i 버튼)
│   └── ExpectedOutcome.tsx # 결과 표시
├── engines/             # 비즈니스 로직
│   └── GTOEngine.ts     # GTO 계산 엔진
├── screens/             # 화면 컴포넌트
│   └── GTOSearchScreen.tsx
├── store/               # 상태 관리
│   └── searchStore.ts   # Zustand 스토어
└── types/               # TypeScript 타입 정의
    └── index.ts
```

## 💡 핵심 기능

### 1. 지능형 GTO 엔진
```typescript
// 실제 포커 전략을 기반한 계산
const result = await GTOEngine.calculateExpectedOutcome({
  position: 'BTN',
  hand: 'AKo', 
  potSize: 15,
  opponents: 2,
  stackDepth: 100
});

// 결과: 승률, EV, 추천액션, 학습포인트
```

### 2. 실시간 반응형 UI
```typescript
// 300ms 디바운싱으로 부드러운 계산
useEffect(() => {
  const timer = setTimeout(() => {
    calculateOutcome(criteria);
  }, 300);
  return () => clearTimeout(timer);
}, [criteria]);
```

### 3. 정보 시스템
```typescript
// 각 요소별 상세 정보와 학습 효과
const infoContent = {
  title: "📍 포지션의 중요성",
  content: "포지션별 전략 상세 설명...",
  expectedEffect: "포지션을 완벽히 이해하면 승률이 15-20% 향상됩니다!"
};
```

## 🎨 UI/UX 디자인 원칙

### 색상 시스템
- 🟢 **초록**: 좋은 결과/강한 액션
- 🟡 **노랑**: 주의/중간 액션  
- 🔴 **빨강**: 위험/약한 액션
- 🔵 **파랑**: 정보 표시

### 정보 계층화
```
1차: 액션 (가장 크고 명확)
2차: 이유 (중간 크기, 요약)  
3차: 상세 (작게, 펼쳐보기)
```

## 📈 기술 스택

- **Frontend**: React Native + TypeScript
- **상태관리**: Zustand  
- **애니메이션**: react-native-animatable
- **UI**: 커스텀 컴포넌트 (Material Design 기반)
- **계산엔진**: 자체 개발 GTO 알고리즘

## 🎯 차별화 포인트

### vs GTO Wizard
- ✅ 단순하고 직관적인 UI
- ✅ 투명한 단일 가격
- ✅ 실시간 학습 효과 미리보기

### vs NTPoker  
- ✅ 정확한 % 계산
- ✅ 다양한 스택 깊이 지원
- ✅ 완성도 높은 기능

### vs PioSolver
- ✅ 모바일 최적화
- ✅ 초보자 친화적
- ✅ 즉시 사용 가능

## 🔮 로드맵

### Phase 1 (현재)
- [x] 기본 GTO 계산 엔진
- [x] 실시간 검색 UI
- [x] 정보 시스템 (i 버튼)
- [x] 기대효과 미리보기

### Phase 2
- [ ] 포스트플랍 분석
- [ ] 상대방 모델링
- [ ] 핸드 히스토리 분석

### Phase 3  
- [ ] AI 기반 개인화
- [ ] 소셜 러닝 기능
- [ ] 실전 연동

## 📱 스크린샷

```
┌─────────────────────────────────────┐
│ 🔍 GTO 상황 검색                    │
├─────────────────────────────────────┤
│ 📍 포지션: [BTN ▼] (i)             │
│ 🎯 핸드: [AKo] (i)                  │
│ 💰 팟: [15BB] (i)                   │
├─────────────────────────────────────┤
│ ✨ 실시간 분석 결과                 │
│ 🎯 승률: 67% 📈                    │
│ 💰 EV: +2.4BB 💚                   │
│ 🎲 추천: 3x Raise [LOW RISK]       │
│ 📚 학습포인트: 포지션 우위 활용     │
└─────────────────────────────────────┘
```

## 🤝 기여하기

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the Branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📄 라이센스

MIT License - 자세한 내용은 [LICENSE](LICENSE) 파일을 참고하세요.

## 📞 연락처

프로젝트 링크: [https://github.com/username/pocket-poker-gto](https://github.com/username/pocket-poker-gto)

---

**"포커를 더 쉽게, 더 스마트하게 배우세요!"** 🃏✨