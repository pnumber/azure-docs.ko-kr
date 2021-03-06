---
title: Azure Analysis Services 서버 관리자 역할에 서비스 사용자 추가 | Microsoft Docs
description: 서버 관리자 역할에 자동화 서비스 사용자를 추가하는 방법을 알아봅니다
services: analysis-services
documentationcenter: ''
author: minewiskan
manager: kfile
editor: ''
ms.assetid: ''
ms.service: analysis-services
ms.workload: data-management
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 03/05/2018
ms.author: owend
ms.openlocfilehash: 8e51b80e184b2b1ff24b1051b55088fbc54c271c
ms.sourcegitcommit: 168426c3545eae6287febecc8804b1035171c048
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/08/2018
---
# <a name="add-a-service-principle-to-the-server-administrator-role"></a>서버 관리자 역할에 서비스 사용자 추가 

 무인 PowerShell 태스크를 자동화하려면 서비스 사용자가 관리할 Analysis Services 서버에 대해 **서버 관리자** 권한이 있어야 합니다. 이 문서에서는 Azure AS 서버에서 서버 관리자 역할에 서비스 사용자를 추가하는 방법을 설명합니다.

## <a name="before-you-begin"></a>시작하기 전에
이 태스크를 완료하기 전에 Azure Active Directory에 등록된 서비스 사용자가 있어야 합니다.

[서비스 사용자 만들기 - Azure Portal](../azure-resource-manager/resource-group-create-service-principal-portal.md)   
[서비스 사용자 만들기 - PowerShell](../azure-resource-manager/resource-group-authenticate-service-principal.md)

## <a name="required-permissions"></a>필요한 사용 권한
이 태스크를 완료하려면 Azure AS 서버에서 [서버 관리자](analysis-services-server-admins.md) 권한이 있어야 합니다. 

## <a name="add-service-principle-to-server-administrators-role"></a>서버 관리자 역할에 서비스 사용자 추가

1. SSMS에서 Azure AS 서버에 연결합니다.
2. **서버 속성** > **보안**에서 **추가**를 클릭합니다.
3. **사용자 또는 그룹 선택**에서 등록된 앱을 이름으로 검색하고 **추가**를 클릭합니다.

    ![서비스 사용자 계정 검색](./media/analysis-services-addservprinc-admins/aas-add-sp-ssms-picker.png)

4. 서비스 사용자 계정 ID를 확인한 다음, **확인**을 클릭합니다.
    
    ![서비스 사용자 계정 검색](./media/analysis-services-addservprinc-admins/aas-add-sp-ssms-add.png)


> [!NOTE]
> AzureRm cmdlet을 사용하는 서버 작업에서, 스케줄러를 실행하는 서비스 사용자는 [Azure RBAC(역할 기반 액세스 제어)](../active-directory/role-based-access-control-what-is.md)에서 리소스에 대한 **소유자**에도 속해야 합니다. 

## <a name="related-information"></a>관련 정보

* [SQL Server PowerShell 모듈 다운로드](https://docs.microsoft.com/sql/ssms/download-sql-server-ps-module)   
* [SSMS 다운로드](https://docs.microsoft.com/sql/ssms/download-sql-server-management-studio-ssms)   


