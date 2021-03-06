---
title: "AKS(Azure Container Service) 할당량 및 지역 가용성"
description: "AKS(Azure Container Service)의 기본 할당량 및 지역 가용성을 다룹니다."
services: container-service
author: david-stanford
manager: timlt
ms.service: container-service
ms.topic: overview
ms.date: 01/16/2018
ms.author: dastanfo
ms.openlocfilehash: eddfab874501fd045820d7da3c968d340fdffe93
ms.sourcegitcommit: f1c1789f2f2502d683afaf5a2f46cc548c0dea50
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 01/18/2018
---
# <a name="quotas-and-region-availability-for-azure-container-service-aks"></a>AKS(Azure Container Service)의 할당량 및 지역 가용성

모든 Azure 서비스에는 리소스와 기능에 대한 특정 기본 제한과 할당량이 있습니다. 다음 섹션에서는 여러 AKS(Azure Container Service) 리소스의 기본 리소스 제한과, Azure 지역의 AKS 서비스 가용성에 대해 자세히 설명합니다.

## <a name="service-quotas-and-limits"></a>서비스 할당량 및 제한

[!INCLUDE [container-service-limits](../../includes/container-service-limits.md)]

## <a name="provisioned-infrastructure"></a>프로비전된 인프라

다른 모든 네트워크, 계산 및 저장소 제한은 프로비전된 인프라에 적용됩니다. 관련 제한은 [Azure 구독 및 서비스 제한](../azure-subscription-service-limits.md)을 참조하세요.

## <a name="region-availability"></a>지역 가용성

AKS(Azure Container Service)는 다음 지역에서 미리 보기로 제공됩니다.
- 미국 동부
- 서유럽
- 미국 중부
- 캐나다 중부
- 캐나다 동부

## <a name="next-steps"></a>다음 단계

특정 기본 제한 및 할당량은 증대가 가능합니다. 이러한 증대를 지원하는 하나 이상의 리소스에 대해 증대를 요청하려면 [Azure 지원 요청][azure-support] (**발급 요청**에 대해 "할당량" 선택)을 제출합니다.

<!-- LINKS - External -->
[azure-support]: https://ms.portal.azure.com/#blade/Microsoft_Azure_Support/HelpAndSupportBlade/newsupportrequest
