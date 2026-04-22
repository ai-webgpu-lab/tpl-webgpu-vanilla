# Results

## 1. 실험 요약
- 저장소: tpl-webgpu-vanilla
- 커밋 해시: d80d247
- 실험 일시: 2026-04-22T06:54:53.975Z -> 2026-04-22T06:54:53.975Z
- 담당자: ai-webgpu-lab
- 실험 유형: `infra`
- 상태: `success`

## 2. 질문
- 최소 WebGPU 스타터가 현재 브라우저에서 adapter/device 획득 또는 fallback 보고를 제대로 남기는가
- triangle sample frame pacing이 첫 baseline result로 재현 가능한가
- 이 결과를 downstream raw WebGPU 실험의 출발점으로 사용할 수 있는가

## 3. 실행 환경
### 브라우저
- 이름: Chrome
- 버전: 147.0.7727.15

### 운영체제
- OS: Linux
- 버전: unknown

### 디바이스
- 장치명: Linux x86_64
- device class: `desktop-high`
- CPU: 16 threads
- 메모리: 16 GB
- 전원 상태: `unknown`

### GPU / 실행 모드
- adapter: WebGPU adapter
- backend: `wasm`
- fallback triggered: `true`
- worker mode: `main`
- cache state: `unknown`
- required features: []
- limits snapshot: {"maxTextureDimension2D":8192,"maxBindGroups":4,"maxBufferSize":1073741824,"maxStorageBufferBindingSize":1073741824,"maxComputeInvocationsPerWorkgroup":256}

## 4. 워크로드 정의
- 시나리오 이름: Minimal WebGPU Starter
- 입력 프로필: single-canvas-960x540
- 데이터 크기: Raw WebGPU canvas starter with adapter/device acquisition and animated triangle sample.; automation=playwright-chromium
- dataset: -
- model_id 또는 renderer: -
- 양자화/정밀도: -
- resolution: 960x540
- context_tokens: -
- output_tokens: -

## 5. 측정 지표
### 공통
- time_to_interactive_ms: 279.5 ms
- init_ms: 0.6 ms
- success_rate: 1
- peak_memory_note: 16 GB reported by browser
- error_type: Failed to acquire webgpu canvas context

### Workload
- avg_fps: 0
- p95_frametime_ms: 0 ms
- scene_load_ms: 0.6 ms
- fallback states: true
- backends: wasm

## 6. 결과 표
| Run | Scenario | Backend | Cache | Mean | P95 | Notes |
|---|---|---:|---:|---:|---:|---|
| 1 | Minimal WebGPU Starter | wasm | unknown | 0 | 0 | scene_load=0.6 ms, fallback=true |

## 7. 관찰
- starter backend는 wasm이고 fallback_triggered=true로 기록됐다.
- frame pacing summary는 avg_fps=0, p95_frametime_ms=0였다.
- playwright-chromium로 수집된 automation baseline이며 headless=true, browser=Chromium 147.0.7727.15.
- 실제 runtime/model/renderer 교체 전 deterministic harness 결과이므로, 절대 성능보다 보고 경로와 재현성 확인에 우선 의미가 있다.

## 8. 결론
- raw WebGPU starter의 첫 baseline raw result와 summary 문서가 연결됐다.
- 다음 단계는 같은 결과 형식을 유지한 채 downstream raw WebGPU 실험 저장소로 전파하는 것이다.
- 실제 device/browser 다변화와 WebGPU/fallback 비교를 추가해야 템플릿 검증이 충분해진다.

## 9. 첨부
- 스크린샷: ./reports/screenshots/01-minimal-webgpu-starter.png
- 로그 파일: ./reports/logs/01-minimal-webgpu-starter.log
- raw json: ./reports/raw/01-minimal-webgpu-starter.json
- 배포 URL: https://ai-webgpu-lab.github.io/tpl-webgpu-vanilla/
- 관련 이슈/PR: -
