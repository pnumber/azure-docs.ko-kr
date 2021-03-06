---
title: "자습서 - Azure Cost Management로 비용 관리 | Microsoft Docs"
description: "이 자습서에서는 비용 할당 및 쇼백과 차지백 보고서를 사용하여 비용을 관리하는 방법을 알아봅니다."
services: cost-management
keywords: 
author: bandersmsft
ms.author: banders
ms.date: 02/27/2018
ms.topic: tutorial
ms.service: cost-management
ms.custom: mvc
manager: carmonm
ms.openlocfilehash: 238964540bffaf8d05148c587462256ce20d87f4
ms.sourcegitcommit: 8c3267c34fc46c681ea476fee87f5fb0bf858f9e
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/09/2018
---
# <a name="tutorial-manage-costs-by-using-azure-cost-management"></a>자습서: Azure Cost Management를 사용한 비용 관리

Azure Cost Management에서 태그를 기준으로 비용을 할당함으로써 비용을 관리하고 쇼백 보고서를 생성합니다. 비용 할당 프로세스는 소비된 클라우드 리소스에 비용을 할당합니다. 비용은 모든 리소스가 태그로 분류되면 완벽하게 할당됩니다. 비용이 할당된 후 쇼백 또는 차지백을 대시보드 및 보고서로 사용자에게 제공할 수 있습니다. 그러나 Cost Management를 사용하기 시작할 때 많은 리소스가 태그되지 않거나 태그하지 못할 수도 있습니다.

예를 들어 엔지니어링 비용에 대한 배상을 얻고자 할 수 있습니다. 리소스 비용을 기반으로 하여 특정 금액이 필요함을 엔지니어링 팀에게 보여줄 수 있어야 합니다. 엔지니어링 팀에게 *엔지니어링*으로 태그가 지정된 모든 소비된 리소스에 대한 보고서를 보여줄 수 있습니다.

이 자습서에서는 다음 방법에 대해 알아봅니다.

> [!div class="checklist"]
> * 사용자 지정 태그를 사용하여 비용을 할당합니다.
> * 쇼백 및 차지백 보고서를 만듭니다.

Azure 구독이 아직 없는 경우 시작하기 전에 [무료 계정](https://azure.microsoft.com/free/?WT.mc_id=A261C142F)을 만듭니다.

## <a name="prerequisites"></a>필수 조건

- Azure 계정이 있어야 합니다.
- Azure Cost Management에 대한 평가판 등록 또는 유료 구독이 있어야 합니다.

## <a name="use-custom-tags-to-allocate-costs"></a>사용자 지정 태그를 사용한 비용 할당

비용 할당을 시작할 때는 먼저 비용 모델을 사용하여 범위를 정의합니다. 비용 모델은 비용을 변경하지 않고 배포합니다. 비용 모델을 만들 때 데이터를 비용 엔터티, 계정 또는 구독별 및 여러 태그별로 나눕니다. 일반적인 예제 태그에는 청구 코드, 비용 센터 또는 그룹 이름이 포함될 수 있습니다. 또한 태그를 사용하면 조직의 다른 부분에 대한 쇼백 또는 차지백을 수행하는 데 도움이 됩니다.

사용자 지정 비용 할당 모델을 만들려면 보고서의 메뉴에서 **비용** &gt; **Cost Management** &gt; **비용 할당 360°**를 선택합니다.

![비용 할당 360 선택](./media/tutorial-manage-costs/cost-allocation-360.png)

**비용 할당 360** 페이지에서 **추가**를 선택한 다음 비용 모델에 사용할 이름 및 설명을 입력합니다. 모든 계정 또는 개별 계정 중에 선택합니다. 개별 계정을 사용하려는 경우 여러 클라우드 서비스 공급자에서 여러 계정을 선택할 수 있습니다. 그런 다음 **분류**를 클릭하여 비용 데이터를 분류하는 검색된 태그를 선택합니다. 모델에 포함하려는 태그(범주)를 선택합니다. 다음 예제에서는 **단위** 태그를 선택합니다.

![예제 비용 모델 분류](./media/tutorial-manage-costs/cost-model01.png)



예제에 분류되지 않은 $14,444가 있습니다(태그 없음).

다음으로, **분류되지 않은 리소스**를 선택하고 할당되지 않은 비용이 있는 서비스를 선택합니다. 그런 다음 비용을 할당하는 규칙을 정의합니다.

예를 들어 Azure Storage 비용을 취하여 Azure VM(가상 머신)에 비용을 동일하게 배포하고자 합니다. 이렇게 하려면 **Azure/Storage** 서비스를 선택하고, **분류된 항목에 비례**를 선택한 다음, **Azure/VM**을 선택합니다. 그런 다음 **만들기**를 선택합니다.

![동일한 배포에 대한 예제 비용 모델 할당 규칙](./media/tutorial-manage-costs/cost-model02.png)



다른 예제에서는 모든 Azure 네트워크 비용을 조직의 특정 비즈니스 부서에 할당하려고 합니다. 이렇게 하려면 **Azure/네트워크** 서비스를 클릭한 다음 **명시적 배포**를 선택합니다. 그런 다음 배포 비율을 100으로 설정하고 비즈니스 부서를 선택합니다. 다음 이미지에서는 **G&amp;A**입니다.

![특정 비즈니스 부서에 대한 예제 비용 모델 할당 규칙](./media/tutorial-manage-costs/cost-model03.png)



분류되지 않은 나머지 모든 리소스의 경우 추가 할당 규칙을 만듭니다.

인스턴스가 예약된 할당되지 않은 AWS(Amazon Web Services)가 있는 경우 **예약된 인스턴스**로 태그된 범주에 할당할 수 있습니다.

비용 할당을 위해 지정한 선택에 관한 정보를 보려면 **요약**을 선택합니다. 사용자의 정보를 저장하여 나중에 추가 규칙에서 계속 작업하려면 **초안으로 저장**을 선택합니다. 또는 사용자의 정보를 저장하여 Cloudyn에서 사용자 비용 할당 모델의 처리를 시작하도록 하려면 **저장 및 활성화**를 선택합니다.

비용 모델의 목록에 **처리 중 상태**인 새 비용 모델이 표시됩니다. Cloudyn 데이터베이스가 비용 모델로 업데이트되려면 다소 시간이 걸릴 수 있습니다. 처리가 완료되면 상태가 **완료됨**으로 업데이트됩니다. 그러면 비용 분석 보고서의 **확장 필터** &gt; **비용 모델**에서 사용자 비용 모델의 데이터를 볼 수 있습니다.

### <a name="category-manager"></a>범주 관리자

범주 관리자는 여러 개의 범주(태그) 값을 병합하여 새로운 값을 만드는 데 도움이 되는 데이터 정리 도구입니다. 범주를 선택하고 규칙을 만들어 기존 값을 병합하는 간단한 규칙 기반 도구입니다. 예를 들어 모두 개발 그룹을 나타내는 **R&amp;D** 및 **dev**에 대한 기존 범주가 있을 수 있습니다.

Cloudyn 포털에서 오른쪽 위의 기어 기호를 클릭하고 **범주 관리자**를 선택합니다. 새 범주를 만들려면 더하기 기호(**+**)를 선택합니다. 범주에 사용할 이름을 입력한 다음, **키** 아래에서 새 범주에 포함시킬 범주 키를 입력합니다.

규칙을 정의하는 경우 OR 조건이 포함된 여러 값을 추가할 수 있습니다. 또한 몇 가지 기본적인 문자열 작업을 수행할 수 있습니다. 두 경우 모두 **규칙** 오른쪽에 있는 줄임표 기호(**…**)를 클릭합니다.

새 규칙을 정의하려면 **규칙** 영역에서 새 규칙을 만듭니다. 예를 들어 **규칙** 아래에 **dev**를 입력한 다음, **동작** 아래에 **R&amp;D**를 입력합니다. 완료되면 새 범주를 저장합니다.

다음 이미지에는 **Work-Load**라는 새 범주에 대해 만들어진 규칙의 예가 나와 있습니다.

![예제 범주](./media/tutorial-manage-costs/category01.png)

### <a name="tag-sources-and-reports"></a>원본 및 보고서에 태그 지정

Cloudyn 보고서에 표시되는 데이터에 태그를 지정하면 다음 세 곳에서 만들어집니다.

- 클라우드 공급자 리소스 API
- 클라우드 공급자 청구 API
- 다음 원본에서 수동으로 만든 태그:
    - Cloudyn 엔터티 태그 - Cloudyn 엔터티에 적용된 사용자 정의 메타데이터
    - 범주 관리자 - 기존 태그에 적용되는 규칙을 기반으로 새 태그를 만드는 데이터 정리 도구

Cloudyn 비용 보고서에서 클라우드 공급자 태그를 보려면 비용 할당 360을 사용하여 사용자 지정 비용 할당 모델을 만들어야 합니다. 이렇게 하려면 **비용** > **비용 관리** > **비용 할당 360**으로 이동하여 원하는 태그를 선택한 다음 태그가 지정되지 않은 비용을 처리하는 규칙을 정의합니다. 그런 다음 새 비용 모델을 만듭니다. 나중에 비용 할당 분석에서 보고서를 확인하여 Azure 리소스 태그를 확인하고 필터링 및 정렬할 수 있습니다.

Azure 리소스 태그는 **비용 할당 분석** 보고서에만 나타납니다.

클라우드 공급자 청구 태그는 모든 비용 보고서에 나타납니다.

Cloudyn 엔터티 태그 및 수동으로 만든 태그는 모든 비용 보고서에 나타납니다.


## <a name="create-showback-and-chargeback-reports"></a>쇼백 및 차지백 보고서 만들기

조직에서 쇼백 및 차지백 수행에 사용하는 메서드는 매우 다양합니다. 그러나 Cloudyn 포털의 대시보드 및 보고서를 각각의 목적에서 기준으로 사용할 수 있습니다. 조직의 구성원들이 필요에 따라 대시보드 및 보고서를 볼 수 있도록 사용자 액세스 권한을 제공할 수 있습니다. 모든 비용 분석 보고서는 사용자에게 자신이 소비하는 리소스를 보여주므로 쇼백을 지원합니다. 또한 사용자가 조직 내에서 해당 그룹에 관련된 비용 또는 사용 현황 데이터를 자세히 살펴보도록 허용할 수 있습니다.

비용 할당의 결과를 보려면 비용 분석 보고서를 열고, 만든 비용 모델을 선택합니다. 그런 다음 비용 모델에서 선택한 하나 이상의 태그로 그룹화를 추가합니다.

![비용 분석 보고서](./media/tutorial-manage-costs/cost-analysis.png)

특정 그룹에서 소비되는 특정 서비스에 초점을 맞춰 보고서를 손쉽게 만들고 저장할 수 있습니다. 예를 들어 Azure VM을 광범위하게 사용하는 부서가 있을 수 있습니다. 소비 및 비용을 보여주도록 Azure VM에서 필터링된 보고서를 만들 수 있습니다.

스냅숏 데이터를 다른 팀에 제공해야 하는 경우 모든 보고서를 PDF 또는 CSV 형식으로 내보낼 수 있습니다.


## <a name="next-steps"></a>다음 단계

이 자습서에서는 다음 방법에 대해 알아보았습니다.

> [!div class="checklist"]
> * 사용자 지정 태그를 사용하여 비용을 할당합니다.
> * 쇼백 및 차지백 보고서를 만듭니다.



데이터에 대한 액세스를 제어하는 방법을 알아 보려면 다음 자습서로 진행하세요.

> [!div class="nextstepaction"]
> [데이터에 대한 액세스 제어](tutorial-user-access.md)
