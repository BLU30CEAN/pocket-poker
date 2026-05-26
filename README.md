# 🃏 pocket-poker

> **GTO를 게임이 아니라 도구로.**
> `BLU30CEAN/pocket-poker` · [live](https://blu30cean.github.io/pocket-poker)

```
$ pocket-poker --status=experimental
```

## 현재 상태

| 항목 | 값 |
| --- | --- |
| Phase | **1 — static landing** |
| 빌드 | `site/` (정적) |
| 배포 | `node ../_ops/cli/ops.mjs deploy pocket-poker` |
| 톤 | `cobalt → magenta` (experiment) · JetBrains Mono 강조 |

## 구조

```
pocket-poker/
├── site/
│   ├── index.html         # 메인 페이지
│   ├── styles.css         # 디자인 토큰 활용
│   ├── design-tokens.css  # _ops 에서 동기화
│   └── app.js             # EV 미니 계산기
└── README.md
```

## EV 미니 계산기

거친 근사식. **솔버 출력이 아니다.**

```
EV (BB) = (handStrength × posMultiplier × oppPenalty − 0.5) × pot

handStrength  핸드 등급 0–1 (AA=1.00 … 72o=0.05)
posMultiplier EP 0.92 / MP 1.00 / CO 1.05 / BTN 1.10 / SB 0.94 / BB 0.85
oppPenalty    1 / (1 + 0.15 × (opponents − 1))
```

## Roadmap

- [x] **Phase 1** — static EV calc
- [ ] **Phase 2** — Expo Web · pre-flop chart 룩업 (수트/페어/오프수트)
- [ ] **Phase 3** — post-flop street planner (board texture × hand class)

## 로컬에서 실행

```bash
# 어느 정적 서버든 OK
npx serve site
# 또는
python -m http.server 5500 -d site
```

## 라이센스

MIT — 자유롭게 가져가서 비틀어보길.
