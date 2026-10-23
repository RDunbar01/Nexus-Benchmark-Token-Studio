# Nexus Benchmark Token Studio

**Version 1.0.1**

훈련 작업의 시간, 유효 토큰 수 및 평가 기록을 명시적으로 측정합니다.

**[브라우저에서 체험하기](https://rdunbar01.github.io/Nexus-Benchmark-Token-Studio/Nexus_Benchmark_Token_Studio_v1_Browser.html)** · [데스크톱 구성 요소 다운로드](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1) · [README](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/README.md)

체험 페이지에서 인터페이스를 살펴보고 **Check WebGPU adapter**를 선택하세요. Python은 필요하지 않습니다. 브라우저 벤치마크는 임시 스크래치 모델과 합성 토큰을 사용하므로 이 테스트에는 모델이나 말뭉치를 다운로드할 필요가 없습니다.

네이티브 패키지 1.0.1, 브라우저 에디션 1.

## 주요 기능

- 합성 토큰과 임시 스크래치 모델을 사용하는 브라우저 벤치마크.
- 지원되는 네이티브 작업을 위한 설치형 PyTorch 테스트.
- 워밍업, 훈련, 평가 및 생성 측정값의 구분.
- 패딩을 유효 토큰으로 세지 않고 설정을 비교할 수 있는 내보내기 기록.

## 기술적 기여

소규모 모델 개발을 위한 재현 가능한 측정 흐름입니다. 합성 속도 테스트를 불러온 모델 및 말뭉치 평가와 구분하여, 초당 토큰 수가 어떤 작업을 측정한 값인지 명확히 합니다.

## 단일 HTML 파일을 사용하는 이유

브라우저 에디션은 인터페이스, JavaScript, CSS와 WGSL 커널을 하나의 HTML 파일에 담습니다. 빌드 과정이나 실행 시 CDN 없이 온라인 체험을 열고, 링크를 공유하고, 내용을 살펴보기 위한 구성입니다. 이 파일에는 브라우저 엔진이 들어 있으며 모델 가중치나 네이티브 PyTorch 백엔드는 포함되지 않습니다.

HTTPS에서 WebGPU 호환 브라우저를 사용하세요. 이 합성 벤치마크는 GGUF 로더나 말뭉치 평가가 아닙니다. 실행 중 네트워크 요청, 네이티브 하드웨어 모니터링, 로컬 서버 연결은 비활성화되어 있습니다. 불러온 모델과 말뭉치를 사용하는 작업에는 전체 설치형 애플리케이션과 지원되는 네이티브 PyTorch 경로가 필요합니다.

[English](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home) · [Français](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.fr) · [日本語](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ja) · [한국어](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/wiki/Home.ko)

## Python 및 네이티브 실행 환경 요구 사항

- **권장 인터프리터는 표준 64비트 CPython 3.12입니다.** 설치 프로그램은 **Python 3.11–3.14**를 안내하지만 부트스트랩 자체가 이 범위를 강제하지는 않습니다. 다른 버전에서 설치 화면이 열린다고 네이티브 백엔드 호환성이 입증되는 것은 아닙니다.
- **새 AMD 런타임 설치에는 Windows 11 25H2의 표준 64비트 CPython 3.11–3.14가 필요하며 free-threaded 빌드는 제외됩니다.** 기존 런타임은 이 설치 조건 검사 전에 테스트되며 런타임 검사를 통과해야만 재사용됩니다. 해당 Python은 설치된 PyTorch wheel과 일치해야 합니다. 더 넓은 Python 버전 호환성을 인증하지 않습니다.
- 포함된 네이티브 검사는 **PyTorch 2.14.0+rocm10.1.0**, HIP, 설정된 RX 7900 XT/XTX를 요구하며 FP32 순전파·역전파 결과가 유한한지 확인합니다. 이 패키지는 Python, AMD 드라이버 또는 컴파일러 필수 구성 요소를 설치하거나 변경하지 않습니다. [AMD 공식 호환성 표](https://rocm.docs.amd.com/en/latest/compatibility/compatibility-matrix.html)를 확인하세요.

이는 설치 프로그램과 런타임의 조건이며 실제 Windows, WebView2, Radeon 또는 전체 모델 검증이 완료되었다는 뜻이 아닙니다. 검사 통과가 모든 정밀도, 컴파일 모드 또는 작업을 검증하지는 않습니다.


## 목적

임시 모델 학습과 지원되는 네이티브 작업의 성능을 측정합니다. 브라우저 에디션은 일회성 모델과 합성 토큰을 사용하는 벤치마크이며, 범용 추론 로더나 불러온 모델의 평가 도구가 아닙니다.

## 에디션 선택

### 브라우저 에디션

HTTPS에서 WebGPU 호환 브라우저를 사용하세요. 이 합성 벤치마크는 GGUF 로더나 말뭉치 평가가 아닙니다. 실행 중 네트워크 요청, 네이티브 하드웨어 모니터링, 로컬 서버 연결은 비활성화되어 있습니다. 불러온 모델과 말뭉치를 사용하는 작업에는 전체 설치형 애플리케이션과 지원되는 네이티브 PyTorch 경로가 필요합니다.

### 설치형 에디션

[1.0.1 패키지](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/tree/main/releases/1.0.1)의 모든 파일을 제공된 배치 그대로 함께 다운로드하세요. 번호가 있는 모든 `.nxd` 데이터 파트를 [Start_Nexus.py](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/Start_Nexus.py) 옆에 두고 지원되는 Python으로 `python Start_Nexus.py`를 실행하세요. 확인하기 전에 [해당 가이드](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/releases/1.0.1/README.md)와 설치 요약을 읽으세요. 각 `.nxd` 파트는 **10,000,000바이트 이하**이며 설치 전 개별 배포 파일은 **20,000,000바이트 미만**입니다. 전체 압축 파일, 복원된 앱, 설치된 파일과 다운로드한 모델은 더 클 수 있습니다. 다른 릴리스를 섞지 마세요. 네이티브 PyTorch 설정과 테스트는 설치형 에디션에만 해당하며 HTML 단독 체험판의 기능이 아닙니다.

## 측정 결과와 한계

CPU 회귀 테스트와 정적 분석/DOM 검사는 실제 Windows/Radeon/WebGPU 하드웨어 검증이 아닙니다. 모델, 코퍼스, 문맥 길이, 배치, 정밀도, 백엔드가 같은 조건에서만 비교하세요. 학습/회복, 프롬프트 처리, 토큰 생성 처리량은 서로 다른 지표입니다. 모든 환경의 호환성이나 최대 속도를 보장하지 않습니다.

## 이용 조건 및 제작

Rich Dunbar / Nexus Emerging Technology. Nexus가 권리를 보유한 자료는 개인적 이용과 내부 상업적 테스트 및 평가에 사용할 수 있습니다. 배포, 수정, 운영 환경 배포 및 그 밖의 상업적 이용에는 명시적인 서면 동의가 필요합니다. 제3자 라이선스와 이미 부여된 권리는 변경되지 않습니다. [라이선스](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/LICENSE) · [평가 추가 허가(영문)](https://github.com/RDunbar01/Nexus-Benchmark-Token-Studio/blob/main/COMMERCIAL_EVALUATION_PERMISSION.md).
