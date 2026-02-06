# Azure Workbooks

Azure Workbooks는 한마디로, Azure Portal에 기본으로 포함된 네이티브 시각화 플랫폼입니다. 

별도의 설치나 별도 비용 없이, 포털 안에서 바로 리포트나 운영 화면을 만들 수 있습니다. 

## 특징
Azure Workbooks의 특징은 다음과 같습니다.

첫 번째는 Build your own로, 내가 직접 만들 수 있습니다. 
즉, 리포트든 분석 내러티브든 트러블슈팅 가이드든, '내가 원하는 스토리'를 빈 캔버스에서 만들 수 있습니다. 

두 번째는 Customize and Extend로, 템플릿을 가져와서 수정하는 방식입니다. 
Azure Portal 안에 이미 제공되는 템플릿이 있고, 커뮤니티 레포에도 샘플이 있어서, 보통은 템플릿을 복사해서 내 환경에 맞게 커스터마이즈할 수 있습니다.

세 번째는 Insights / Curated Experiences입니다. 
Cosmos DB, 네트워크, SQL, ADX, 스토리지, AVD, Sentinel 같은 서비스들은 이미 Workbooks 기반으로 정리된 인사이트 화면을 제공하고 있습니다. 
즉, 포털에서 'Insights'를 누르면 사실상 그 기저는 Workbooks로 구성되어 있다고 보시면 됩니다.

## Reporting canvas
실제 Azure Workbooks 화면을 살펴보도록 하겠습니다.

Azure 포털 홈에서 모니터링 메뉴로 이동합니다.
모니터링 화면의 좌측 메뉴에서 "통합 문서"를 클릭합니다.

통합 문서 | 갤러리 화면이 보여지는데, 여기서 Virtual Machines의 **성능** 항목을 클릭합니다. (생성된 Virtual Machines가 없는 경우에는 다른 항목을 선택하여도 됩니다.)

![Azure Workbooks - Canvas](/lectures/visualization-workbooks-grafana/images/azure-workbooks-reporting-canvas.png)

여기 보시는 화면은 Workbooks가 왜 '리포팅 캔버스'라고 부르는지 잘 보여줍니다.

상단에 Subscription, Workspace, Time Range 같은 범위를 잡는 컨트롤이 있고, 그 결과가 아래 그리드에 바로 반영됩니다. 

이런 구성이 가능한 이유가 Workbooks가 파라미터 기반으로 동작하기 때문입니다.

그리고 이 그리드 자체가 단순 표가 아니라, 상황에 따라선 클릭해서 더 깊게 들어가도록 구성할 수도 있습니다. 
운영자 입장에서는 '전체 현황을 보고 → 이상한 대상을 골라서 → 더 깊게 파고드는' 흐름을 한 화면에서 만들 수 있습니다

즉, Dashboard가 '상태판'이라면, Workbooks는 '분석 리포트'에 더 가깝다고 이해하시면 됩니다.

## 새로 만들기
새로운 Workbooks을 생성하는 것도 가능합니다.

- 홈 > Azure Workbooks > Create > Quick > Empty로 시작해도 되고
- 홈 > Azure Workbooks > Create > 기존에 있는 템플릿을 수정해도 됩니다.

![Azure Workbooks - New](/lectures/visualization-workbooks-grafana/images/azure-workbooks-parameter.png)

Workbooks는 보통 파라미터부터 잡고 시작하면 만들기가 편합니다. 예를 들어 구독, 리소스 범위, 지역, 시간 범위 같은 것들이요. 이런 파라미터를 만들어 두면, 사용자가 화면에서 선택하는 값에 따라 아래의 쿼리나 메트릭 차트가 동적으로 바뀌는 구조를 만들 수 있습니다. 

그 다음 단계는 '데이터 소스'를 고르는 건데요. 메트릭을 쓸 수도 있고, 로그를 KQL로 쿼리할 수도 있고, 필요하면 다른 데이터 소스도 붙일 수 있습니다. Workbooks는 데이터 소스 폭이 넓어서, 예를 들어 Azure Resource Graph, ARM, ADX, Custom endpoint 같은 것들도 연결이 가능합니다. 

정리하면, 파라미터(입력) → 쿼리/메트릭(데이터) → 시각화(표현) 이 세 가지를 조합해서 '내러티브'를 만든다고 보시면 됩니다.

## 인사이트
Azure Workbooks는 포털에서 제공되는 인사이트에서도 사용됩니다.

**홈 > 모니터링 > 인사이트 > Virtual Machines > Performance탭** 으로 이동합니다.

![Azure Workbooks - Insights](/lectures/visualization-workbooks-grafana/images/azure-workbooks-insights.png)

이 화면은 VM 같은 리소스에서 제공되는 Workbooks/Insights 예시라고 보시면 됩니다.

중요한 포인트는, Workbooks가 Azure Portal 안에서 리소스 경험(Experience)의 일부로 자연스럽게 노출됩니다. 

즉, 사용자가 'Workbooks를 만들러 간다'기보다, 운영하다가 필요한 화면을 열었는데 그게 Workbooks 기반인 경우가 많습니다.

이런 큐레이션된 인사이트들은 '바로 쓸 수 있는 시작점'을 제공하고, 필요하면 그걸 복사해서 우리 조직 상황에 맞게 수정해 운영 표준 리포트로 만드는 방식도 가능합니다.

화면 우측의 View Workbooks를 통해서 미리 만들어져 있는 여러 workbooks들로 이동할 수 있고,

화면 좌측의 insights 메뉴 하단을 보면, 여러 종류의 리소스들에 대한 insights로 이동할 수도 있습니다. 
해당 insight에는 리소스에 맞는 각각의 workbooks들이 제공됩니다.

## 장점
Azure Workbooks의 장점을 정리하면,

1. 첫째, **Interactive**입니다.

    Workbooks는 필터와 파라미터로 스코프를 관리하고, 상황에 따라 다른 블레이드나 다른 워크북으로 링크를 걸어서 '클릭하면서 탐색하는' 흐름을 만들 수 있습니다. 
즉, 단순 시각화가 아니라 상호작용 기반 분석 경험을 만드는 데 강합니다.

2. 둘째, **Integrated**입니다.

    저장, 공유, 대시보드에 핀(pin) 같은 통합 기능이 있고, 더 중요한 건 Workbooks가 ARM 리소스로 관리될 수 있다는 점입니다. 
    
    그래서 템플릿이나 ARM 템플릿 기반으로 배포/관리하는 시나리오도 가능합니다. 

3. 셋째, **Multiple Data Sources**입니다.

    Workbooks는 Logs, Metrics, Health 뿐 아니라 Azure Resource Graph, ARM, ADX, JSON, Custom endpoint, 그리고 Prometheus까지 연결할 수 있습니다. 
    
    그리고 결정적으로 서로 다른 데이터 소스를 쿼리한 결과를 Merge로 합치거나 Join해서 한 화면에 보여줄 수 있습니다. 

    이게 **워크북은 스토리 빌더**라는 표현과 잘 맞는 부분입니다. 

## Workbooks의 유형들

마지막으로 Workbooks의 '유형'을 살펴보도록 하겠습니다. 
Workbooks는 갤러리에서 크게 세 부류로 구분됩니다.

![Azure Workbooks - types](/lectures/visualization-workbooks-grafana/images/azure-workbooks-types.png)

- 첫 번째는 **Public Templates**입니다.Microsoft가 게시한 바로 사용 가능한 템플릿이고, 템플릿을 열면 '임시 워크북(Transient workbook)'이 만들어져서, 마음껏 파라미터를 바꿔 분석해도 원본 템플릿은 망가지지 않습니다. 
그리고 저장하면 그때 내 워크북으로 남는 구조입니다. 

- 두 번째는 **Workbooks**입니다. 내가 직접 만들었거나 누군가가 공유해준 워크북들이고, 보통은 저장되는 순간 ARM 리소스로 관리되기 때문에 접근 제어도 Azure RBAC 모델을 따르게 됩니다. 

- 세 번째는 **My Templates**입니다.개인이든 조직이든 템플릿으로 배포해 재사용하게 만드는 방식이고, 결국 ‘표준 템플릿’을 만들어서 팀이 복사해 쓰게 하는 운영 모델에 잘 맞습니다. 

갤러리에서도 Workbooks / Public Templates / My Templates 같은 탭으로 구분해서 볼 수 있습니다.

[Azure Dashboard](dashboard.md) << **Azure Workbooks** >> [Azure Managed Grafana](azure-managed-grafana.md)