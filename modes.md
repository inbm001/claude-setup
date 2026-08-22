# caveman / ponytail 모드

설치하면 모든 폴더, 모든 세션에서 자동으로 켜진다. 세션 시작 시 훅이 활성화한다.

| 플러그인 | 역할 |
|---|---|
| ponytail | 코드를 줄인다. 안 만드는 쪽을 먼저 본다 |
| caveman | 말을 줄인다. 군더더기를 뺀다 |

겹치지 않는다.

## 켜고 끄기

입력창에 그대로 입력한다.

| 하고 싶은 것 | 입력 |
|---|---|
| caveman 끄기 | `stop caveman` 또는 `/caveman off` |
| caveman 켜기 | `/caveman full` |
| ponytail 끄기 | `stop ponytail` 또는 `/ponytail off` |
| ponytail 켜기 | `/ponytail full` |
| 둘 다 끄기 | `normal mode` |

세기: `lite` `full` `ultra` — 예) `/caveman lite`

세션 단위다. 이 대화에서 꺼도 새 대화는 다시 `full` 로 시작한다.

영구히 끄려면 플러그인을 제거한다.

```bash
claude plugin uninstall caveman
```

## 언제 끄나

- 문서 작성, 메일 초안, 설명문 — caveman 이 말투를 압축해서 어색해진다. `stop caveman`
- ponytail 은 코드에만 관여하므로 켜둬도 무해하다

## 차이 비교

요청: "API 응답에 캐시 좀 추가해줘"

**둘 다 꺼짐**

> 네, 캐싱을 추가하겠습니다. 몇 가지 접근 방식이 있는데요, 첫째는 인메모리 캐시를 직접 구현하는 것이고, 둘째는 Redis 같은 외부 저장소를 쓰는 방법입니다. 요청량과 데이터 일관성 요구사항에 따라 선택이 달라집니다. 우선 간단하게 시작하되 나중에 확장 가능하도록 `CacheManager` 클래스를 만들고, TTL과 최대 크기를 설정으로 뺀 뒤 인터페이스를 두어 백엔드를 교체할 수 있게 하는 구조를 제안드립니다. 어떻게 진행할까요?

**caveman 만** — 말투만 짧아짐. 만드는 양은 그대로

> `CacheManager` 클래스 추가. TTL·최대 크기 설정으로 분리. 인터페이스 두면 나중에 Redis 교체 가능. 코드:

**ponytail 만** — 말은 길지만 안 만드는 쪽을 봄

> 표준 라이브러리로 충분합니다. `functools.lru_cache` 를 fetch 함수에 붙이면 끝입니다. 별도 캐시 클래스는 만들지 않았습니다 — 지금 요구사항에서는 `lru_cache` 가 부족하다는 근거가 없기 때문입니다. 나중에 측정해서 한계가 드러나면 그때 교체하시면 됩니다.
>
> ```python
> @lru_cache(maxsize=1000)
> ```

**둘 다**

> `@lru_cache(maxsize=1000)` fetch 함수에 붙임. 캐시 클래스 안 만듦. lru_cache 모자란 게 측정되면 그때 교체.

| | 결과물 | 설명 길이 |
|---|---|---|
| 기본 | 클래스 + 인터페이스 + 설정 | 김 |
| caveman | 클래스 + 인터페이스 + 설정 | 짧음 |
| ponytail | 한 줄 | 김 |
| 둘 다 | 한 줄 | 짧음 |
