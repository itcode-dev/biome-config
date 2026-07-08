# @itcode-dev/biome-config

[English](./README.md)

itcode.dev 프로젝트에서 공용으로 사용하는 [Biome](https://biomejs.dev) 설정 프리셋입니다. 모든 규칙에 왜 켜져 있는지, 왜 꺼져 있는지, 왜 그렇게 튜닝했는지를 설명하는 주석이 달려 있어서, 설정 파일 자체가 문서 역할도 합니다.

> [!NOTE]
> - 이 설정은 지극히 개인적인 취향에 따라 구성되어 보편적인 컨벤션과 맞지 않는 부분도 있습니다.
> - 모든 옵션을 명시하여 다소 경직된 설정일 수 있습니다.
> - 일반적으로 저 자신의 여러 프로젝트를 구성할 때 사용하기 위한 목적으로 개발되었습니다.

## 설치

```bash
pnpm add -D @itcode-dev/biome-config @biomejs/biome
```

```bash
npm install -D @itcode-dev/biome-config @biomejs/biome
```

## 사용법

프로젝트의 `biome.jsonc`에서 프리셋을 extends 하면 됩니다:

```jsonc
{
	"$schema": "https://biomejs.dev/schemas/2.5.2/schema.json",
	"extends": ["@itcode-dev/biome-config"]
}
```

## 제공되는 프리셋

| Export | Biome 버전 | 설명 |
| --- | --- | --- |
| `@itcode-dev/biome-config` | latest | 항상 최신 지원 Biome 버전을 따라갑니다. Biome 자체의 카테고리 변화(예: `nursery` 규칙의 승격/제거)에 맞춰 규칙 구성도 함께 바뀝니다. |
| `@itcode-dev/biome-config/2.4` | `2.4.x` | Biome `2.4` 규칙 스키마 기준으로 고정된 프리셋입니다. |
| `@itcode-dev/biome-config/2.2.0` | `2.2.x` | Biome `2.2` 규칙 스키마 기준으로 고정된 프리셋입니다. |

`@itcode-dev/biome-config`가 업데이트될 때마다 규칙이 바뀌는 게 부담스럽다면, 위 표의 버전 고정(`/2.x`) export를 사용하세요. Biome을 업그레이드해도 린트 규칙이 흔들리지 않습니다.

### `nursery` 규칙

Biome의 `nursery` 카테고리는 실험적인 규칙들을 모아두는 곳이라, 릴리즈마다 이름이 바뀌거나 안정 카테고리로 승격되거나 아예 삭제되기도 합니다. 이 변동성 때문에 Biome이나 이 패키지를 업그레이드할 때마다 설정이 깨질 수 있습니다. 이런 걸 신경 쓰고 싶지 않다면, 위 프리셋들의 `no-nursery` 버전을 사용하세요 — `nursery` 카테고리 전체를 꺼줍니다:

```jsonc
{
	"$schema": "https://biomejs.dev/schemas/2.5.2/schema.json",
	"extends": ["@itcode-dev/biome-config/no-nursery"]
}
```

모든 프리셋에는 대응하는 `no-nursery` export가 있습니다: `@itcode-dev/biome-config/no-nursery`, `@itcode-dev/biome-config/2.4/no-nursery`, `@itcode-dev/biome-config/2.2.0/no-nursery`.

## 포맷 컨벤션

- 들여쓰기: 탭 (너비 4)
- 라인 너비: 128
- 줄바꿈: LF
- 따옴표: JS/TS는 홑따옴표, JSX와 CSS는 쌍따옴표
- 세미콜론: 항상 사용
- 후행 쉼표: 사용 안 함

이 설정과 모든 린터 규칙은 이 프리셋을 extends 한 뒤 여러분의 `biome.jsonc`에서 자유롭게 오버라이드할 수 있습니다.

## 호환성

이 패키지는 peerDependency로 `@biomejs/biome` `^2.2.0` 이상을 요구합니다. 프로젝트에 설치된 Biome 버전에 맞는 프리셋을 extends 하세요 (위 표 참고).

## 라이선스

[Apache-2.0](./LICENSE)
