---
title: Azure Logic Apps에서 통합 계정 만들기, 연결, 삭제 또는 이동 | Microsoft Docs
description: 통합 계정을 만들고 논리 앱에 연결하는 방법
services: logic-apps
documentationcenter: .net,nodejs,java
author: divyaswarnkar
manager: anneta
editor: ''
ms.assetid: d3ad9e99-a9ee-477b-81bf-0881e11e632f
ms.service: logic-apps
ms.workload: integration
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 02/23/2017
ms.author: LADocs; divswa
ms.openlocfilehash: fb1d0ceb26c5ed792f22051e2af10a7572200bdc
ms.sourcegitcommit: 8aab1aab0135fad24987a311b42a1c25a839e9f3
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/16/2018
---
# <a name="what-is-an-integration-account"></a>통합 계정이란?

통합 계정은 엔터프라이즈 통합 앱, 특히 논리 앱에서 거래 업체, 규약, 맵, 스키마, 인증서 등과 같은 B2B 아티팩트에 대한 액세스 및 관리할 수 있는 방법을 제공합니다. 이 액세스를 제공하려면 통합 계정과 논리 앱 모두에 *동일한 Azure 위치*가 있는지 확인한 후 통합 계정을 논리 앱에 연결합니다.

## <a name="create-an-integration-account"></a>통합 계정 만들기

1. [Azure Portal](http://portal.azure.com "Azure Portal")에 로그인합니다. 

2. Azure의 주 메뉴에서 **모든 서비스**를 선택합니다. 검색 상자에 “통합”을 입력한 다음, **통합 계정**을 선택합니다.

   ![통합 계정 만들기](./media/logic-apps-enterprise-integration-accounts/account-1.png)

3. 페이지 맨 위에 있는 **추가**를 선택합니다.

   ![[추가] 선택](./media/logic-apps-enterprise-integration-accounts/account-3.png)

4. 통합 계정의 이름을 지정하고 사용할 Azure 구독을 선택합니다. 새 **리소스 그룹**을 만들거나 기존 리소스 그룹을 선택할 수 있습니다. **위치**를 선택하여 통합 계정 및 **가격 책정 계층**을 호스트합니다. 준비되면 **만들기**를 선택합니다.

   ![통합 계정의 세부 정보를 제공합니다.](./media/logic-apps-enterprise-integration-accounts/account-4.png)

   Azure에서는 선택한 위치에서 통합 계정을 프로비전하고 1분 내에 완료해야 합니다.

5. 페이지를 새로 고칩니다. 새 통합 계정이 나열되어 있습니다.

   ![새 통합 계정이 표시됩니다.](./media/logic-apps-enterprise-integration-accounts/account-5.png) 

그런 다음 만든 통합 계정을 논리 앱에 연결합니다. 

## <a name="link-an-integration-account-to-a-logic-app"></a>논리 앱에 통합 계정 연결

논리 앱에 통합 계정의 거래 업체, 규약, 맵 및 스키마와 같은 B2B 아티팩트에 대한 액세스 권한을 부여하려면 통합 계정을 논리 앱에 연결해야 합니다. 

1. Azure Portal에서 논리 앱을 선택하고 논리 앱의 위치를 확인합니다.

   ![논리 앱을 선택하고 위치를 확인합니다.](./media/logic-apps-enterprise-integration-accounts/linkaccount-1.png)

2. **설정**에서 **통합 계정**을 선택합니다.

   !["통합 계정" 선택](./media/logic-apps-enterprise-integration-accounts/linkaccount-2.png)

3. **통합 계정 선택** 목록에서 논리 앱에 연결하려는 통합 계정을 선택합니다. 연결을 완료하려면 **저장**을 선택합니다.

   ![통합 계정 선택](./media/logic-apps-enterprise-integration-accounts/linkaccount-3.png)

   통합 계정이 논리 앱에 연결되어 있고 이제는 통합 계정의 모든 아티팩트를 논리 앱에서 사용할 수 있음을 보여 주는 알림이 표시됩니다.

   ![논리 앱이 통합 계정에 연결됩니다.](./media/logic-apps-enterprise-integration-accounts/linkaccount-5.png)

통합 계정이 논리 앱에 연결되었으므로 논리 앱 내에서 B2B 커넥터를 사용할 수 있습니다. 일반적인 B2B 커넥터 일부에는 XML 유효성 검사 및 플랫 파일 인코딩/디코딩이 포함되어 있습니다.  

## <a name="delete-your-integration-account"></a>통합 계정 삭제

1. Azure의 주 메뉴에서 **모든 서비스**를 선택합니다. 검색 상자에 "통합"을 입력한 다음, **통합 계정**을 선택합니다.

   ![통합 계정 찾기](./media/logic-apps-enterprise-integration-accounts/account-1.png)

2. 삭제하려는 통합 계정을 선택합니다.

    ![삭제할 통합 계정 선택](./media/logic-apps-enterprise-integration-accounts/account-5.png)

3. 메뉴에서 **삭제**를 선택합니다.

    !["삭제" 선택](./media/logic-apps-enterprise-integration-accounts/delete.png)

4. 통합 계정을 삭제하도록 선택합니다.

## <a name="move-your-integration-account"></a>통합 계정 이동

다른 Azure 구독 또는 리소스 그룹으로 통합 계정을 이동하려면 다음과 같은 단계를 수행합니다. 통합 계정을 이동한 후에 새 리소스 ID를 사용할 수 있도록 모든 스크립트를 업데이트해야 합니다.

1. Azure의 주 메뉴에서 **모든 서비스**를 선택합니다. 검색 상자에 "통합"을 입력한 다음, **통합 계정**을 선택합니다.

   ![통합 계정 찾기](./media/logic-apps-enterprise-integration-accounts/account-1.png)

2. 이동하려는 통합 계정을 선택합니다. **설정** 아래에서 **속성**을 선택합니다.

   ![이동할 통합 계정을 선택합니다. [설정] 아래에서 [속성]을 선택합니다.](./media/logic-apps-enterprise-integration-accounts/move.png)

3. 사용자 통합 계정과 연결된 리소스 그룹 또는 Azure 구독을 변경합니다.

   ![리소스 그룹 변경 또는 구독 변경 선택](./media/logic-apps-enterprise-integration-accounts/move-2.png)

## <a name="next-steps"></a>다음 단계

* [규약에 대해 자세히 알아보기](../logic-apps/logic-apps-enterprise-integration-agreements.md "엔터프라이즈 통합 규약에 대해 알아보기")  

