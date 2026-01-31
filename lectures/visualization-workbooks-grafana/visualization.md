# Azure Monitor의 시각화 옵션들 (Azure Monitor Visualizations)

## '모니터링'은 왜 어렵고, 왜 '시각화'가 핵심일까?

초심자 관점에서 모니터링의 첫 경험은 대체로 이렇습니다.

> "서비스가 느려졌대요. 근데… 어디가 문제인지 모르겠어요."

> 로그는 많고, 그래프는 여기저기 흩어져 있고, 화면을 보는 사람(운영자/개발자/관리자/경영진)에 따라 보고 싶은 것도 다릅니다.

여기서 시각화(Visualization) 는 단순히 예쁜 그래프가 아니라, "지금 무슨 일이 벌어지는지"를 한 눈에 보여 주고, 필요하면 원인 분석으로 드릴다운할 수 있게 해주는 마법의 언어가 됩니다. 

<img src='https://learn.microsoft.com/en-us/azure/azure-monitor/fundamentals/media/overview/overview-blowout-20230707-opt.svg#lightbox'>

이번 강좌에서는 Azure Monitor의 시각화 옵션들에 대해서 살펴보게 됩니다.

- [모니터링이 어려운 이유](./challenges-with-application-monitoring.md)
- [Azure에서 제공하는 시각화 옵션 4가지](options.md)
    - [Azure Dashboard](dashboard.md)
    - [Azure Workbooks](workbooks.md)
    - [Azure Managed Grafana](azure-managed-grafana.md)
    - [Power BI](power-bi.md)
- [내 상황에서는 '어떤 시각화 옵션'을 선택하면 되는가?](when-to-use.md)

## 참고 문서
- [Azure Monitor 개요](https://learn.microsoft.com/ko-kr/azure/azure-monitor/fundamentals/overview)
- [Azure Monitor에서 데이터 시각화](https://learn.microsoft.com/ko-kr/azure/azure-monitor/visualize/best-practices-visualize)
- [Azure 통합 문서](https://learn.microsoft.com/ko-kr/azure/azure-monitor/visualize/workbooks-overview)
- [Azure Workbooks 템플릿](https://learn.microsoft.com/ko-kr/azure/azure-monitor/visualize/workbooks-templates)
- [프로그래밍 방식으로 통합 문서 관리](https://learn.microsoft.com/ko-kr/azure/azure-monitor/visualize/workbooks-automate)
- [Grafana를 사용하여 Azure Monitor 데이터 시각화](https://learn.microsoft.com/ko-kr/azure/azure-monitor/visualize/visualize-grafana-overview)