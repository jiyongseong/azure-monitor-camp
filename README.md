# Azure Monitor Camp

Azure Monitor Camp는 **Azure Monitor 강좌** 와 **Hands-on Lab** 을 한 곳에 모아,  
Azure 환경(그리고 필요 시 hybrid/other cloud)에서 관측 가능성(Observability)을 **처음부터 끝까지** 직접 구현해 보는 교육용 리포지토리입니다.

Metrics / Logs / Traces 기반의 모니터링 데이터를 **수집 → 저장 → 분석 → 시각화 → 알림/자동 대응** 흐름으로 익히고, 다음의 항목들에 대해서 단계적으로 살펴보게 됩니다.

- Azure Monitor Logs(Log Analytics)
- Application Insights
- Azure Monitor Agent(AMA)
- Data Collection Rule(DCR)
- Alerts/Action Groups
- Azure Workbooks, 
- Managed Prometheus & Managed Grafana

✅ Azure Monitor는 지속적으로 업데이트되고 있으므로 실습 화면 및 UI는 현재 포털과 일부 차이가 있을 수 있습니다.

---

## 🎯 목표 

- Azure Monitor의 큰 그림(데이터 플랫폼 + 도구 체계) 이해
- Logs(Microsoft Sentinel 연계 포함 가능) / Metrics / Traces의 차이와 활용 지점 체감
- Log Analytics(KQL)로 **문제 분석/탐지**를 직접 수행
- Alerts + Action Groups + (선택) Automation으로 **운영 대응** 흐름 구현
- Workbooks / Dashboards / (선택) Grafana로 **관측 데이터 시각화**
- AMA + DCR 기반으로 **표준화된 수집 구성**(확장, 재사용, 운영 편의성) 경험

---

## 👥 대상 독자 

- Azure Monitor를 처음 접하는 엔지니어 / 운영자 / 솔루션 아키텍트
- 고객 워크샵, 사내 교육, Azure Monitor 세션 진행자
- "모니터링을 대충 붙이는 수준"을 넘어, **운영 가능한 형태로 설계**하고 싶은 분

---

## 🧩 사전 준비 사항

- Azure Subscription (Owner/Contributor 권한 권장)
- 리소스 생성 권한: Log Analytics Workspace / Application Insights / Alerts / Action Groups 등
- 기본적인 Azure Portal 사용 경험
- (선택) 로컬 도구
  - Azure CLI 또는 PowerShell
  - VS Code + KQL 확장(선택)
- (선택) 실습 확장 시
  - VM(Windows/Linux) 또는 AKS 클러스터
  - 샘플 앱(.NET/Java/Node 중 하나) 또는 컨테이너 워크로드

> ⚠️ 비용 주의: 일부 실습은 VM/AKS/데이터 수집량에 따라 과금이 발생할 수 있습니다.  
> Lab 가이드에 "삭제 단계"가 포함되어 있지 않더라도, 마지막에는 lab에서 생성한 리소스그룹 또는 리소스들을 삭제하는 것을 권장합니다.

---

## 📁 폴더 구조 (목표로 하는 구조. 변경될 예정입니다.)

azure-monitor-camp/  
├─ labs/                        # 실습 과제 (문서, 스크립트, 샘플)  
│  ├─ in-a-day/                  # 'Azure Monitor in a Day' 트랙  
│  │  ├─ lab0-overview/  
│  │  ├─ lab1-log-analytics-workspace/  
│  │  ├─ lab2-application-insights/  
│  │  ├─ lab3-ama-dcr-vm-insights/  
│  │  ├─ lab4-diagnostic-settings-activity-logs/  
│  │  ├─ lab5-kql-troubleshooting/  
│  │  ├─ lab6-alerts-action-groups/  
│  │  ├─ lab7-alert-processing-rules/  
│  │  └─ lab8-automation-runbooks/  
│  ├─ by-feature/                # 기능별(토픽별) 심화 랩  
│  └─ scenarios/                 # 시나리오 기반(end-to-end) 랩  
├─ lectures/                     # 강의 자료 (개념/아키텍처/데모 스토리)  
│  ├─ azure-monitor-whatis/  
│  ├─ logs-metrics-traces/  
│  ├─ kql-fundamentals/  
│  ├─ alerts-automation/  
│  └─ visualization-workbooks-grafana/  
└─ README.md

---

## 🛠️ 'Azure Monitor in a Day' Hands-on Lab

Azure Monitor의 핵심을 빠르게 훑기 위한 **입문용 end-to-end 트랙**입니다.

- **Lab 0 - Azure Monitor Overview**
  - Azure Monitor가 다루는 데이터 종류(Metrics/Logs/Traces)와 전체 흐름 소개

- **Lab 1 - Log Analytics Workspace**
  - Workspace 생성, 접근 제어, 보존 기간/상태 점검(헬스/알림) 등 기본 구성

- **Lab 2 - Application Insights (App Observability)**
  - Application Insights 리소스 생성
  - (선택) 샘플링/일일 캡/이상 징후 알림 등 기본 튜닝
  - (선택) 진단 로그 연계

- **Lab 3 - VM Monitoring (AMA + DCR + VM Insights)**
  - Azure Monitor Agent(AMA) 배포
  - Data Collection Rule(DCR)로 이벤트 로그/시스템 로그/성능 데이터 수집 구성
  - VM Insights 활성화

- **Lab 4 - Diagnostic settings & Activity Logs**
  - Azure 리소스 로그/Activity Log를 Log Analytics로 보내는 표준 패턴 구성
  - “어떤 로그를 어디로 보낼지” 운영 설계 포인트 정리

- **Lab 5 - KQL Troubleshooting Basics**
  - 자주 쓰는 KQL 패턴(필터/집계/조인/타임윈도우)
  - 운영 질문(“언제부터?”, “무엇이?”, “어디서?”)에 답하는 쿼리 작성

- **Lab 6 - Alerts & Action Groups**
  - Action Group 생성(Email/Teams/Webhook 등)
  - Metric Alert / Log Alert 작성
  - 알림 메시지 표준화(운영자가 바로 조치할 수 있게)

- **Lab 7 - Alert Processing Rules**
  - 특정 시간대/조건에서 알림 억제(Suppress) 등 노이즈 제어

- **Lab 8 - Automated Responses**
  - (선택) Runbook/Logic Apps/Functions 등과 연계해 자동 대응 플로우 구성

---

## 🧪 Hands-on Lab by Feature (심화/토픽별)

Azure Monitor의 기능별 실습입니다. (지속적으로 추가 예정)

### 📌 Azure Monitor Logs (Log Analytics / KQL)
- KQL 패턴 모음(운영형 쿼리 템플릿)
- Custom logs / Logs Ingestion API (선택)
- 비용/보존/테이블 설계 팁(선택)

### 📈 Metrics & Metrics Explorer
- 플랫폼 메트릭 이해
- Dimension 기반 분석
- Metric Alert 설계 패턴

### 🧭 Application Insights (APM)
- 트랜잭션/의존성/실패 분석
- 분산 추적(Trace) 기초 (선택: OpenTelemetry)

### 🧰 AMA & DCR (표준 수집 설계)
- "수집 표준" 만들기: DCR 템플릿화
- Windows Event / Syslog / IIS logs 등 연결

### 🧩 [Visualization](/lectures/visualization-workbooks-grafana/visualization.md)
- [모니터링이 어려운 이유](/lectures/visualization-workbooks-grafana/challenges-with-application-monitoring.md)
- [Azure에서 제공하는 시각화 옵션 4가지](/lectures/visualization-workbooks-grafana/options.md)
    - [Azure Dashboard](/lectures/visualization-workbooks-grafana/dashboard.md)
    - [Azure Workbooks](/lectures/visualization-workbooks-grafana/workbooks.md)
    - [Azure Managed Grafana](/lectures/visualization-workbooks-grafana/azure-managed-grafana.md)
    - [Power BI](/lectures/visualization-workbooks-grafana/power-bi.md)
- [내 상황에서는 '어떤 시각화 옵션'을 선택하면 되는가?](/lectures/visualization-workbooks-grafana/when-to-use.md)

### 🌐 Network Monitoring
- Network Watcher / Connection Monitor
- Flow logs / Traffic Analytics (선택)

### 🚨 Alerts & Automation
- Action Groups / Alert rules / Processing rules
- (선택) ITSM/ServiceNow/Teams 연동 시나리오

---

## 🚀 시작하기 (Getting Started)
리포지토리 클론
```bash
git clone https://github.com/jiyongseong/azure-monitor-camp.git
```

## 🤝 기여 방법 (Contributing)
프로젝트에 대한 제안이나 수정 사항은 Issue 또는 Pull Request로 언제든지 환영합니다.

- 오타 수정
- 실습 절차 개선
- 신규 lab 추가 
- 운영 시나리오 추가

## 📄 License
이 프로젝트는 누구나 자유롭게 공유하고 활용할 수 있습니다.

## ✨ Maintainer
* **[Ji Yong Seong (MSFT)](https://github.com/jiyongseong)** 