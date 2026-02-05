# Azure에서 제공하는 시각화 옵션 4가지

## Azure Monitor

먼저 모니터링을 위해서 왜 Azure Monitor가 필요한지부터 짧게 짚고 가겠습니다.
오늘날 컴퓨팅 환경은 점점 더 분산되어 있고, 애플리케이션은 수많은 컴포넌트로 구성돼 있고, 서비스와 애플리케이션은 계속 바뀌고, 보안과 컴플라이언스 요구사항도 계속 커지고 있습니다. 
이런 환경에서는 "어디가 문제인지", "지금 무슨 일이 벌어지고 있는지"를 한 번에 보기 어렵습니다. 

Azure Monitor는 이런 문제를 해결하기 위해서, 운영 관점에서 가시성(Visibility) 확보 → 인사이트(Insights) 획득 → 최적화(Optimization)로 이어지는 흐름을 제공하는 플랫폼이라고 이해하시면 됩니다. 

<img src='https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/media/overview/overview-blowout-20230707-opt.svg#lightbox'>

그림 왼쪽의 Data Sources는 "데이터가 발생하는 곳"입니다. 여기에는 애플리케이션과 워크로드, 인프라, Azure 플랫폼 자체의 리소스들, 그리고 고객이 직접 만든 커스텀 소스까지 포함됩니다. 즉 Azure 안에서만이 아니라, 필요하면 다른 클라우드나 온프레미스 환경까지 확장해서 관찰할 수 있습니다.

그 다음 가운데 영역이 Data Collection, Routing, and Transform, 즉 "수집하고, 라우팅하고, 필요한 형태로 변환하는 구간"입니다.Azure Monitor가 단순히 로그를 저장하는 시스템이 아니라, 수집 경로 자체를 표준화하고 관리할 수 있다는 점에 주목해야 합니다. 
App SDK, Agent, DCR(Data Collection Rules), Diagnostic settings 같은 요소들이 있는데, 이런 기능들을 통해 애플리케이션/인프라에서 나오는 텔레메트리를 Azure Monitor의 데이터 플랫폼으로 자연스럽게 흘려보낼 수 있습니다. 

다음은 중앙의 핵심 부분인 Data Platform입니다.
Azure Monitor의 중심에는 데이터 저장소가 있고, 저장소에는 가장 중요한 두 가지 데이터 타입이 Metrics와 Logs가 저장됩니다. 
즉 "측정값"과 "로그"가 Azure Monitor의 기본 데이터라고 볼 수 있습니다.
Logs와 Metrics 외에도 Traces, Changes 같은 항목이 함께 배치되어 있는데, Azure Monitor가 단순히 수치와 텍스트 로그만이 아니라, 애플리케이션 추적이나 변경 이력 같은 신호도 함께 다루면서 운영 분석을 가능하게 만든다는 의미로 이해할 수 있습니다. 

오른쪽으로 가면 Consumption, 즉 "활용" 영역입니다. 이 부분이 실제 운영자나 개발자 입장에서 체감하는 기능들이 모여 있는 구간이고, 크게 네 덩어리로 나뉩니다: Insights, Visualize, Analyze, Respond 입니다. 

두 번째에 있는 Visualize이 글의 주제인 "시각화 옵션"들과 연결됩니다. 
Visualize 영역에는 Workbooks, Dashboards, Power BI, Grafana 같은 도구들이 들어가 있고, 같은 데이터 플랫폼을 기반으로 서로 다른 관점과 목적의 시각화를 지원합니다. 
즉, 데이터는 같아도 운영 대시보드 중심, 조사/분석 중심, 장기 KPI 리포팅 중심, Prometheus 및 멀티 플랫폼 관점 등 목적에 따라 표현 방식이 달라진다고 보시면 됩니다. 

정리하면,
첫째, Azure Monitor는 다양한 소스에서 나오는 신호를 표준적인 수집 파이프라인으로 모읍니다. 
둘째, 중심에는 Metrics와 Logs를 핵심으로 하는 데이터 플랫폼이 있고, 여기서 인사이트/시각화/분석/대응이 이어집니다. 
셋째, 마지막으로 Azure 밖의 도구들과도 연결될 수 있도록 통합(Integrate)과 확장 경로를 제공합니다.

## Azure Monitor 시각화 옵션 한눈에 보기

### Azure Dashboard
![Azure Dashboard example](https://learn.microsoft.com/en-us/azure/azure-monitor/media/visualizations/dashboard.png)
Azure Dashboard는 Azure Portal 안에서 여러 타일을 한 화면에 모아, 운영에 중요한 정보를 **빠르게 훑어보는 "요약 상태판"** 으로 쓰기 좋습니다. 특히 Log Analytics 쿼리 결과도 차트로 시각화해서 대시보드에 올릴 수 있고, 공유 시에는 Azure RBAC로 접근 권한이 통제됩니다.

### Azure Workbooks
![Azure Workbooks visualizations](https://learn.microsoft.com/en-us/azure/azure-monitor/visualize/media/workbooks-overview/visualizations.png)

Azure Workbooks는 Azure Portal 안에서 텍스트 + 로그 쿼리 + 메트릭 + 파라미터를 한 화면에 조합해, 분석 내용을 "이야기처럼" 구성할 수 있는 유연한 캔버스입니다. 여러 데이터 소스를 함께 사용해 통합된 인터랙티브 경험을 만들 수 있어서, 여러 리소스를 가로지르는 end-to-end 모니터링 화면을 만들 때 특히 유용합니다.

### Azure Managed Grafana
![Grafana visualizations](https://learn.microsoft.com/en-us/azure/azure-monitor/media/visualizations/grafana.png)

Grafana는 여러 데이터 소스의 메트릭/로그/트레이스를 쿼리해 운영 중심(operational) 대시보드를 만드는 데 강한 오픈 플랫폼이며, Azure는 이를 시각화하는 옵션으로 Grafana를 제공하고 있습니다. 특히 Azure Monitor와 연계하는 두 가지 방식(Portal 내 Grafana 대시보드 / 완전 관리형 Azure Managed Grafana)을 안내하고, 다양한 데이터 소스를 지원하는 관리형 옵션도 소개합니다.

### Power BI
![Power BI report example](https://learn.microsoft.com/en-us/azure/azure-monitor/media/visualizations/power-bi.png)

Power BI는 운영자가 실시간으로 보는 화면이라기보다, 비즈니스 중심 KPI 대시보드와 장기 트렌드(장기 KPI) 리포트를 만드는 데 적합합니다. Azure Monitor에서는 로그 쿼리 결과를 Power BI 데이터셋으로 가져와, 여러 데이터 소스 결합이나 리포트 공유 같은 Power BI 기능을 활용할 수 있습니다.

[모니터링이 어려운 이유](challenges-with-application-monitoring.md) << **Azure에서 제공하는 시각화 옵션 4가지** >> [Azure Dashboard](dashboard.md)