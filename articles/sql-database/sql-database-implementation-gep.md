---
title: Azure SQL Database Azure 사례 연구 - GEP | Microsoft Docs
description: GEP이 SQL Database를 사용하여 더 많은 글로벌 고객에게 도달하고 보다 높은 효율성을 달성하는 방법을 알아봅니다.
services: sql-database
author: CarlRabeler
manager: craigg
ms.service: sql-database
ms.custom: reference
ms.topic: article
ms.date: 01/10/2017
ms.author: carlrab
ms.openlocfilehash: 093f891ea9dd36a2766d0a797c4f0a67b11aa8a4
ms.sourcegitcommit: 8aab1aab0135fad24987a311b42a1c25a839e9f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="azure-gives-gep-global-reach-and-greater-efficiency"></a>Azure를 통한 GEP의 글로벌 고객 접근 및 효율성 개선
![GEP 로고](./media/sql-database-implementation-gep/geplogo.png)

GEP는 전 세계의 조달 책임자가 비즈니스 작업, 전략 및 재무 성능에 미치는 영향을 최대화할 수 있도록 하는 소프트웨어와 서비스를 제공 합니다. 이 회사는 컨설팅 서비스 및 관리되는 서비스 외에도, 클라우드 기반의 포괄적인 조달 소프트웨어 플랫폼인 SMART by GEP®를 제공합니다. 그러나 GEP는 자체 온-프레미스 데이터 센터에서 SMART by GEP와 같은 솔루션을 지원하려고 할 때 한계에 부딪혔습니다. 필요한 투자금은 폭발적으로 증가했으며 다른 국가의 규정 요구 때문에 필요한 투자금을 확보하는 것도 요원했습니다. GEP는 클라우드로 전환하여 IT 리소스를 확보함으로써, IT 운영에 대한 부담을 줄이고, 전 세계 고객을 위해 새로운 가치를 개발하는 데 집중할 수 있게 되었습니다.

## <a name="expanding-services-and-growth-by-using-azure"></a>Azure를 사용하여 서비스 및 성장 확장
SMART by GEP 고객은 이 플랫폼의 기능과 사용 편의성을 좋아합니다. 고객은 언제 어디서나 어떤 장치에서든(노트북, 태블릿 또는 휴대폰) 프로세스를 관리할 수 있습니다. Microsoft Azure를 전환하여 GEP는 새로운 시장으로 확장할 수 있는 빠른 성장 및 잠재력을 갖출 수 있게 되었습니다. GEP의 기술 담당 부사장인 Dhananjay Nagalkar에 따르면 "Microsoft Azure는 우리가 민첩하게 서비스를 확장하고, 전 세계 고객의 규정 요구를 충족하는 데 도움이 되는 지역 데이터 센터를 제공함으로써 GEP의 성공에 중요한 역할을 했습니다."

## <a name="the-limitations-of-a-do-it-yourself-datacenter"></a>자체 데이터 센터의 제한 사항
2013년에 GEP 책임자들은 고객 기반이 증가할 때 확장성 및 성능을 보장하는 방법이 필요하다고 인식했습니다. "기존 데이터 센터를 사용하여 해당 요청을 충족하기 위해서는 우리의 인프라 및 IT 리소스를 획기적으로 확장해야 했을 것입니다. 해당 투자금 및 기간도 엄청났을 것입니다."라고 Nagalkar는 설명했습니다. 온-프레미스 실제 및 가상 머신에서는 GEP에서 감당할 수 없는 비용으로 포괄적인 구성, 관리, 크기 조정, 백업 및 패치를 수행해야 합니다. 한편, 클라우드 서비스는 GEP가 증가하는 대규모 IT 작업을 관리하는 대신, 개발에 더 집중하도록 하는 간편성과 편리성을 제공합니다. Nagalkar는 GEP가 클라우드로 마이그레이션하여 인프라 구입, 구성 및 관리 오버헤드를 줄일 수 있을 것이라는 사실을 알았습니다.

또한 GEP는 일부 글로벌 시장 진입을 막는 규제 장벽을 극복하는 방안도 필요했습니다. GEP의 많은 잠재적인 유럽 고객의 경우, 규정 준수를 위해 로컬 지리적 위치에 데이터를 저장해야 했습니다. 하지만 GEP가 여러 데이터 센터를 구축하는 것은 실용적이지 않았을 것입니다. "광범위한 인프라 투자와 IT 인력 비용이 매출에 상당한 영향을 미치고 있습니다.”라고 Nagalkar는 말했습니다. "결과적으로 우리는 로컬에 저장된 데이터를 원하는 잠재 고객에게 눈을 돌려야 했습니다.”

Nagalkar는 클라우드 솔루션이 이 딜레마에 대한 해답이 될 수 있다는 것을 알았습니다. GEP는 글로벌 서비스를 제공하는 클라우드 공급자로 전환할 수 있게 되면서 데이터를 고객의 실제 위치에 더 가깝게 저장하여 고객의 규정 및 성능 요구를 보다 잘 충족할 수 있게 되었습니다.

## <a name="finding-smooth-skies-in-the-cloud"></a>클라우드에서 원활한 방안 찾기
Nagalkar와 그의 팀은 여러 클라우드 옵션을 연구했으나 대부분은 GEP가 서비스를 구성하고 관리하기 위해 IT 리소스에 과도하게 투자해야만 하는 IaaS(infrastructure-as-a-service) 기반 솔루션이었습니다. Azure PaaS(platform-as-a-service) 솔루션이 훨씬 적합한 것으로 판명되었습니다.

"Azure를 사용하게 되면서 GEP는 데이터베이스 관리, 가상 컴퓨터 구성, 패치 또는 기타 인프라 관리 작업을 처리할 필요가 없습니다.” "대신, 우리는 우리가 가장 잘하는 일에 집중할 수 있습니다. 즉, 조달 분야의 전문성을 활용하여 고객을 위한 결과를 전달하는 소프트웨어를 작성하는 것과 같은 일 말이죠.”라고 Nagalkar는 말했습니다. 

실제로, Azure로 전환하면서 GEP는 고객을 위한 더 많은 기능을 동시에 사용하도록 지원하면서 IT 운영 직원을 축소할 수 있었습니다.

GEP는 전 세계적으로 Azure 데이터 센터를 활용하여 유럽과 아시아 전역까지 쉽게 시장을 넓힐 수 있습니다. 이러한 글로벌 데이터 센터를 통해 GEP는 민첩하게 규모를 조정하고, 로컬로 저장된 데이터에 대한 고객 요구를 충족하여 대기 시간을 줄이고 규정 요건을 충족할 수 있습니다.

## <a name="smart-by-gep-architecture"></a>SMART by GEP 아키텍처
GEP는 Azure에서 SMART by GEP를 새롭게 구축했습니다. GEP의 주요 동기는 GEP가 온-프레미스에서 얻었던 혜택과 비교할 때 Azure SQL Database로 경험할 수 있던 뛰어난 확장성, 가동 중단 시간 감소, 유지 관리 비용 절감이었습니다. 그러나 클라우드로 전환한 후에 GEP는 클라우드에서 고객의 요구에 보다 빠르게 응답하기 위한 빠른 프로토타입 개발 및 린엔지니어링과 같은 새로운 개발 기회를 알게 되었습니다. GEP는 Azure에서 개발을 수행함으로써 개발자들이 온-프레미스에서 직면할 수 있는 소프트웨어 라이선스 문제도 해결할 수 있게 되었습니다. GEP는 많은 다른 Azure 서비스를 사용하여 SMART by GEP을 쉽고 빠르게 지속적으로 향상시키고 있지만 SMART by GEP의 핵심은 Azure SQL Database입니다.

![SMART by GEP 아키텍처](./media/sql-database-implementation-gep/figure1.png) 그림 1. SMART by GEP 아키텍처

## <a name="structured-data"></a>구조화된 데이터
SMART by GEP 응용 프로그램의 핵심에는 엔터프라이즈 조달 관리 솔루션을 지원하는 Azure SQL Database 인스턴스가 있습니다. GEP는 SMART by GEP를 엔지니어링할 때 Azure SQL Database가 해당 아키텍처에 아주 완벽하다는 것을 알게 되었습니다. 이 데이터베이스는 최고 수준의 데이터 보호를 달성하고 규정 요건을 충족할 수 있게 해줄 수 있었습니다. GEP는 다음을 비롯하여 Azure SQL Database가 제공하는 여러 데이터 보호 계층을 사용합니다.

* 투명한 데이터 암호화를 통해 미사용 데이터 암호화
* Azure SQL Database를 Azure Active Directory에 통합하여 인증 보안 유지
* 행 수준 보안을 사용하여 해당 데이터 하위 집합에 대한 액세스 제한
* 정책을 통해 실시간으로 데이터 마스킹
* Azure SQL Database 감사를 통해 데이터베이스 이벤트 추적

> "우리는 주요 코드를 변경하지 않고 성능에 최소한의 영향만 미치면서 이러한 모든 옵션을 사용할 수 있습니다.”라고 Nagalkar는 말했습니다.
> 
> 

GEP는 Azure SQL Database에 기본적으로 제공되는 내결함성 기능 때문에 온-프레미스에서 효율적으로 엔지니어링할 수 있는 것보다 훨씬 더 큰 재해 복구 기능을 자동으로 갖추게 되었습니다. GEP는 여러 다른 지리적 지역에서 읽을 수 있는 여러 활성 온라인 보조 복제본(Always On 가용성 그룹)과 함께 Azure SQL Database의 활성 지역 복제 기능을 사용하여 고가용성 쌍을 형성합니다. 지역에 걸쳐 SMART by GEP 데이터를 복제하는 것은 전체 지역에서 재해가 발생할 경우 GEP가 최소 RPO(복구 지점 목표) 및 RTO(복구 시간 목표)를 사용하여 고객 데이터를 쉽게 복구할 수 있음을 의미합니다.

각 SMART by GEP 고객에게는 두 개의 Azure SQL Database 인스턴스가 있습니다. 하나는 OLTP(온라인 트랜잭션 처리)용이고 다른 하나는 분석용입니다(예: 고객 지출 및 보고서 분석). Azure SQL Database의 탄력적 풀을 사용하여 GEP는 수천 개의 데이터베이스를 전역적으로 쉽게 관리하여 예측할 수 없는 데이터베이스 리소스 요구를 처리할 수 있습니다. 탄력적 풀은 GEP가 비용을 제어하면서 과다한 프로비전 또는 부족한 프로비전 없이 필요에 따라 고객 데이터베이스 규모를 조정할 수 있도록 합니다. 또한 PaaS 서비스이기 때문에 GEP는 자동 업그레이드를 통해 새로운 Azure SQL Database 기능을 얻게 됩니다.

## <a name="unstructured-and-semi-structured-data"></a>비구조화된 데이터 및 반구조화된 데이터
그러나 일부 SMART by GEP 고객 데이터에는 덜 엄격하게 구조화된 저장소가 필요합니다. 이러한 데이터 유형의 경우, GEP는 Azure Blob Storage, Azure Table Storage 및 Azure Redis Cache를 사용합니다. Azure Blob 저장소는 SMART by GEP 사용자가 응용 프로그램에 업로드하는 모든 첨부 파일을 보관합니다. SMART by GEP는 CSS 스타일시트 및 JavaScript 파일과 같은 정적 콘텐츠도 여기에 저장합니다.

GEP는 SMART by GEP 로그 데이터와 같이 고객이 직접 사용하지 않는 데이터를 Azure Table Storage에 저장합니다. 이를 통해 GEP는 데이터 스키마 설정에 대해 걱정할 필요 없이 제한 없는 비용 효율적 저장소와 빠른 검색 시간을 얻을 수 있습니다. GEP는 마스터 캐시에 대해 Azure Redis Cache를 사용합니다.

## <a name="authentication-and-routing"></a>인증 및 라우팅
Azure ACS(Access Control Service)는 SMART by GEP 사용자에게 소프트웨어에 서명하기 위한 다양한 옵션을 제공합니다. Azure ACS는 Active Directory Domain Services, Ping Identity, OneLogin, SiteMinder 등의 SAML(Security Assertion Markup Language)을 사용하여 인증 데이터를 교환하는 모든 ID 공급자와 페더레이션할 수 있습니다. 이를 통해 GEP는 사용자 자격 증명 저장 및 고객 암호 정책 유지 관리 문제를 걱정할 필요 없이 고객을 위해 SSO(Single Sign-On)를 구현할 수 있습니다.

일단 로그인된 고객은 SMART by GEP에서 올바른 비즈니스 리소스에 액세스할 수 있습니다. GEP는 Azure Traffic Manager를 사용하여 고객의 모바일 장치 및 브라우저 세션에서 발생하는 요청을 리디렉션하고 부하를 분산합니다.

## <a name="other-azure-services"></a>기타 Azure 서비스
GEP는 다양한 Azure 서비스를 사용하여 고객에 요구에 응답할 수 있는 SMART by GEP를 구현합니다. GEP는 Azure 클라우드 서비스(웹 및 작업자 역할)를 사용하여 응용 프로그램 프레젠테이션 및 보안 비즈니스 논리 서비스를 호스트합니다. 클라우드 서비스는 개발자가 온-프레미스 데이터 센터를 사용할 때 필요한 것보다 훨씬 짧은 시간 안에 IT 부서의 도움 없이 IAC(infrastructure as code)를 관리하고 새로운 SMART by GEP 응용 프로그램을 배포할 수 있도록 합니다. GEP 개발자는 클라우드 서비스 스테이징 환경을 사용하여 현재 프로덕션 배포에 영향을 주지 않고 새 릴리스를 테스트할 수 있습니다. 일단 테스트가 끝나면 GEP는 Azure 클라우드 서비스의 VIP 교환 기능을 사용하여 1분 안에 스테이징 코드를 프로덕션 슬롯으로 이동할 수 있으므로 배포에 따른 가동 중지가 감소됩니다.

응용 프로그램 대기 시간을 줄이기 위해 GEP는 Azure CDN(Content Delivery Network)을 사용하여 Azure Blob 저장소(예: CSS 및 JavaScript 파일)에 저장된 정적 콘텐츠를 사용자에게 가까운 Edge 서버에 추가합니다. GEP는 Azure Service Bus를 사용하여 느슨한 결합 및 비동기 통신을 통해 게시-구독부터 부분적인 CQRS(Command Query Responsive Segregation) 및 계층형 아키텍처에 이르는 응용 프로그램-아키텍처 패턴을 지원합니다. GEP는 Azure Media Services를 사용하여 고객 지원 서비스를 개선합니다. GEP는 Azure Media Services에서 사용자 지원 비디오를 쉽게 게시할 수 있다는 사실을 알게 되었습니다. 이러한 비디오는 일반적인 사용자 질문에 답변하므로 GEP의 고객 지원 담당자의 지원 업무 부담을 덜어주면서 SMART by GEP 사용자 만족도를 높이는 데 도움이 됩니다.

이 회사는 매일 SMART by GEP에서 생성되는 수천 개의 트랜잭션 전자 메일을 전송하기 위해 SendGrid.NET API를 사용하여 Azure와 통합하고 있습니다. GEP 개발자는 이 작업을 쉽게 수행할 수 있습니다. Azure용 SendGrid 추가 기능을 Azure Marketplace에서 바로 사용할 수 있기 때문입니다. GEP 개발자는 Microsoft Visual Studio에서 바로 SendGrid NuGet 패키지를 사용하여 SMART by GEP를 구성할 수 있습니다. 또한 GET IT 직원은 Azure에서 직접 이 소프트웨어의 SendGrid 전자 메일 트래픽을 모니터링할 수 있습니다.

마지막으로, SMART by GEP는 Azure Virtual Machines(Azure IaaS 서비스)를 사용하여 엔지니어링 시점에 적합하지 않아 나중에 SaaS(software-as-a-service) 또는 PaaS 솔루션과 대체할 응용 프로그램 및 서비스를 호스트합니다. 예를 들어 GEP는 SAP, Oracle, PeopleSoft, JD Edwards, Microsoft Dynamics GP 및 Lawson와 같은 고객의 온-프레미스 ERP(엔터프라이즈 리소스 계획) 시스템 및 고객 SaaS 솔루션과의 B2B(기업 간) 통합을 위해 통합 API 서비스를 호스트함으로써 송장과 같은 조달 문서를 효율적으로 교환합니다.

> "Microsoft Azure 클라우드에서 SMART by GEP를 구축함으로써 GEP뿐 아니라 고객의 조달 업무를 위한 온-프레미스 IT에 대한 필요가 완전히 해소되었습니다." 
> 
> — 기술 솔루션 담당 부사장, Dhananjay Nagalkar
> 
> 

## <a name="expand-customer-satisfaction-without-expanding-it"></a>IT 확장 없이 고객 만족도 강화
온-프레미스 데이터 센터에서 Azure로 마이그레이션하고 Azure 플랫폼에서 SMART by GEP를 완전히 새로 구축하였기 때문에 GEP는 해당 인프라 또는 IT 직원을 확장할 필요 없이 확장성과 유연성을 강화할 수 있게 되었습니다. 실제로 이 회사는 4년 넘게 IT 리소스를 추가하지 않았습니다. Azure의 편리한 PaaS 모델을 통해 GEP는 공급업체 지원 및 운영 관리 비용을 절감할 수 있었습니다. 결과적으로, GEP는 소프트웨어 개발에 리소스를 투입할 수 있게 되었습니다. 클라우드에서 개발을 진행하면서 GEP 개발자들은 IT 부서와의 조정 작업에 시간을 투자하거나 온-프레미스 라이선스 요구를 걱정하지 않고 새 아이디어를 빠르게 테스트할 수 있게 되었습니다. Azure SQL Database는 GEP가 고객에게 뛰어난 서비스와 성능을 제공할 수 있도록 지원합니다.

## <a name="more-information"></a>자세한 정보
* GEP 홈페이지: [GEP](http://www.gep.com)
* Smart by GEP: [Smart by GEP](http://www.smartbygep.com)

## <a name="gep-contributors"></a>GEP 참가자
* GEP의 부소장, 설계자 Huzaifa Matawala
* GEP의 엔지니어링 관리자 Sathyan Narasingh
* GEP의 데이터베이스 설계자 Deepa Velukutty

