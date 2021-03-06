---
title: "응용 프로그램에 사용자 및 그룹을 할당하는 방법 | Microsoft Docs"
description: "액세스 권한을 부여하도록 응용 프로그램에 사용자 할당"
services: active-directory
documentationcenter: 
author: ajamess
manager: mtillman
ms.assetid: 
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 07/11/2017
ms.author: asteen
ms.openlocfilehash: d670b2400fc1ac50afdcc8b809a1d482c3219686
ms.sourcegitcommit: d87b039e13a5f8df1ee9d82a727e6bc04715c341
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/21/2018
---
# <a name="how-to-assign-users-and-groups-to-an-application"></a>응용 프로그램에 사용자 및 그룹을 할당하는 방법

사용자가 특정 응용 프로그램에 대해 아래의 작업을 수행할 수 있으려면 먼저 액세스 권한을 부여하도록 **응용 프로그램에 할당**해야 합니다.

-   **응용 프로그램의 URL로 직접 이동**(SP 시작 로그온이라고도 함)하여 응용 프로그램에 액세스합니다.

-   응용 프로그램의 **속성** 페이지에서 **사용자 액세스 URL**(IDP 시작 로그온이라고도 함)을 사용하여 응용 프로그램에 액세스합니다.

-   [응용 프로그램 액세스 패널](https://myapps.microsoft.com/) 또는 모바일 응용 프로그램에 응용 프로그램이 나타나는지 확인합니다.

-   [Office 365 응용 프로그램 시작 관리자](https://support.office.com/article/Meet-the-Office-365-app-launcher-79f12104-6fed-442f-96a0-eb089a3f476a)에 응용 프로그램이 나타나는지 확인합니다.

## <a name="methods-to-assign-applications-with-azure-active-directory"></a>Azure Active Directory로 응용 프로그램을 할당하는 방법 

Azure Active Directory로 응용 프로그램을 할당할 수 있는 3가지 방법이 있습니다.

-   [관리자 권한으로 응용 프로그램에 직접 사용자 할당](#assign-a-user-directly-as-an-administrator)

-   [관리자 권한으로 응용 프로그램에 직접 그룹 할당](#assign-a-group-directly-to-an-application-as-an-administrator)

-   [셀프 서비스 응용 프로그램 액세스를 활성화하여 사용자가 자신의 응용 프로그램을 찾을 수 있도록 함](#enable-self-service-application-access-to-allow-users-to-find-their-own-applications)

## <a name="assign-a-user-directly-as-an-administrator"></a>관리자 권한으로 직접 사용자 할당

응용 프로그램에 하나 이상의 사용자를 직접 할당하려면 다음 단계를 수행합니다.

1.  [**Azure Portal**](https://portal.azure.com/)을 열고 **전역 관리자** 권한으로 로그인합니다.

2.  왼쪽 주 탐색 메뉴의 맨 위에서 **모든 서비스**를 클릭하여 **Azure Active Directory 확장**을 엽니다.

3.  필터 검색 상자에 **“Azure Active Directory**”를 입력하고 **Azure Active Directory** 항목을 선택합니다.

4.  Azure Active Directory 왼쪽 탐색 메뉴에서 **엔터프라이즈 응용 프로그램**을 클릭합니다.

5.  **모든 응용 프로그램**을 클릭하여 모든 응용 프로그램의 목록을 봅니다.

  * 여기에 표시하려는 응용 프로그램이 표시되지 않으면 **모든 응용 프로그램 목록**의 맨 위에서 **필터** 컨트롤을 사용하고 **표시** 옵션을 **모든 응용 프로그램**으로 설정합니다.

6.  목록에서 사용자를 할당하려는 응용 프로그램을 선택합니다.

7.  응용 프로그램이 로드되면 응용 프로그램의 왼쪽 탐색 메뉴에서 **사용자 및 그룹**을 클릭합니다.

8.  **사용자 및 그룹** 목록의 맨 위에서 **추가** 단추를 클릭하여 **할당 추가** 창을 엽니다.

9.  **할당 추가** 창에서 **사용자 및 그룹** 선택기를 클릭합니다.

10. **이름 또는 전자 메일 주소로 검색** 검색 상자에 할당하려는 사용자의 **전체 이름** 또는 **전자 메일 주소**를 입력합니다.

11. 목록의 **사용자** 위로 마우스를 이동하여 **확인란**을 표시합니다. 사용자의 프로필 사진이나 로고 옆의 확인란을 클릭하여 사용자를 **선택됨** 목록에 추가합니다.

12. **선택 사항:** **둘 이상의 사용자를 추가**하려는 경우 **이름 또는 전자 메일 주소로 검색** 검색 상자에 다른 **전체 이름** 또는 **전자 메일 주소**를 입력하고 확인란을 클릭하여 이 사용자를 **선택됨** 목록에 추가합니다.

13. 사용자 선택이 완료되면 **선택** 단추를 클릭하여 응용 프로그램에 할당되도록 사용자 및 그룹의 목록에 추가합니다.

14. **선택 사항:** **할당 추가** 창에서 **역할 선택** 선택기를 클릭하여 선택한 사용자에게 할당할 역할을 선택합니다.

15. **할당** 단추를 클릭하여 선택한 사용자에게 응용 프로그램을 할당합니다.

잠시 후 선택한 사용자는 솔루션 설명 섹션에 설명된 메서드를 사용하여 이러한 응용 프로그램을 시작할 수 있습니다.

## <a name="assign-a-group-directly-to-an-application-as-an-administrator"></a>관리자 권한으로 응용 프로그램에 직접 그룹 할당

응용 프로그램에 하나 이상의 그룹을 직접 할당하려면 다음 단계를 수행합니다.

1.  [**Azure Portal**](https://portal.azure.com/)을 열고 **전역 관리자** 권한으로 로그인합니다.

2.  왼쪽 주 탐색 메뉴의 맨 위에서 **모든 서비스**를 클릭하여 **Azure Active Directory 확장**을 엽니다.

3.  필터 검색 상자에 **“Azure Active Directory**”를 입력하고 **Azure Active Directory** 항목을 선택합니다.

4.  Azure Active Directory 왼쪽 탐색 메뉴에서 **엔터프라이즈 응용 프로그램**을 클릭합니다.

5.  **모든 응용 프로그램**을 클릭하여 모든 응용 프로그램의 목록을 봅니다.

  * 여기에 표시하려는 응용 프로그램이 표시되지 않으면 **모든 응용 프로그램 목록**의 맨 위에서 **필터** 컨트롤을 사용하고 **표시** 옵션을 **모든 응용 프로그램**으로 설정합니다.

6.  목록에서 사용자를 할당하려는 응용 프로그램을 선택합니다.

7.  응용 프로그램이 로드되면 응용 프로그램의 왼쪽 탐색 메뉴에서 **사용자 및 그룹**을 클릭합니다.

8.  **사용자 및 그룹** 목록의 맨 위에서 **추가** 단추를 클릭하여 **할당 추가** 창을 엽니다.

9.  **할당 추가** 창에서 **사용자 및 그룹** 선택기를 클릭합니다.

10. **이름 또는 메일 주소로 검색** 검색 상자에 할당하려는 그룹의 **전체 그룹 이름**을 입력합니다.

11. 목록의 **그룹** 위로 마우스를 이동하여 **확인란**을 표시합니다. 그룹의 프로필 사진이나 로고 옆의 확인란을 클릭하여 사용자를 **선택됨** 목록에 추가합니다.

12. **선택 사항:** **둘 이상의 그룹을 추가**하려는 경우 **이름 또는 메일 주소로 검색** 검색 상자에 다른 **전체 그룹 이름**을 입력하고 확인란을 클릭하여 이 그룹을 **선택됨** 목록에 추가합니다.

13. 그룹 선택이 완료되면 **선택** 단추를 클릭하여 응용 프로그램에 할당되도록 사용자 및 그룹의 목록에 추가합니다.

14. **선택 사항:** **할당 추가** 창에서 **역할 선택** 선택기를 클릭하여 선택한 그룹에 할당할 역할을 선택합니다.

15. **할당** 단추를 클릭하여 선택한 그룹에 응용 프로그램을 할당합니다.

잠시 후 선택한 그룹 내 사용자는 솔루션 설명 섹션에 설명된 메서드를 사용하여 이러한 응용 프로그램을 시작할 수 있습니다. 동적 그룹인 경우 이러한 할당된 그룹 내 사용자에 대해 표시되는 이러한 할당에 약간의 추가 처리 지연이 있을 수 있습니다.

## <a name="enable-self-service-application-access-to-allow-users-to-find-their-own-applications"></a>셀프 서비스 응용 프로그램 액세스를 활성화하여 사용자가 자신의 응용 프로그램을 찾을 수 있도록 함

셀프 서비스 응용 프로그램 액세스는 사용자가 응용 프로그램을 직접 검색하도록 하고 경우에 따라 비즈니스 그룹이 해당 응용 프로그램에 대한 액세스를 승인하도록 허용하는 유용한 방법입니다. 비즈니스 그룹이 해당 액세스 패널에서 암호 Single Sign-On 응용 프로그램 권한에 대해 해당 사용자에게 할당된 자격 증명을 관리하도록 허용할 수 있습니다.

응용 프로그램에 대한 셀프 서비스 응용 프로그램 액세스를 사용하려면 다음 단계를 수행합니다.

1.  [**Azure Portal**](https://portal.azure.com/)을 열고 **전역 관리자** 권한으로 로그인합니다.

2.  왼쪽 주 탐색 메뉴의 맨 위에서 **모든 서비스**를 클릭하여 **Azure Active Directory 확장**을 엽니다.

3.  필터 검색 상자에 **“Azure Active Directory**”를 입력하고 **Azure Active Directory** 항목을 선택합니다.

4.  Azure Active Directory 왼쪽 탐색 메뉴에서 **엔터프라이즈 응용 프로그램**을 클릭합니다.

5.  **모든 응용 프로그램**을 클릭하여 모든 응용 프로그램의 목록을 봅니다.

   * 여기에 표시하려는 응용 프로그램이 표시되지 않으면 **모든 응용 프로그램 목록**의 맨 위에서 **필터** 컨트롤을 사용하고 **표시** 옵션을 **모든 응용 프로그램**으로 설정합니다.

6.  셀프 서비스 액세스를 활성화하려는 응용 프로그램을 목록에서 선택합니다.

7.  응용 프로그램이 로드되면 응용 프로그램의 왼쪽 탐색 메뉴에서 **셀프 서비스**를 클릭합니다.

8.  이 응용 프로그램에 대한 셀프 서비스 응용 프로그램 액세스를 활성화하려면 **사용자가 이 응용 프로그램에 대한 액세스를 요청하도록 허용하시겠습니까?** 토글을 **예**로 전환합니다.

9.  다음으로 이 응용 프로그램에 대한 액세스를 요청하는 사용자에 추가되어야 하는 그룹을 선택하려면 레이블 **할당된 사용자는 어느 그룹에 추가되어야 합니까?** 옆의 선택기를 클릭하고 그룹을 선택합니다.

10. **선택 사항:** 사용자의 액세스를 허용하기 전에 비즈니스 승인을 필요로 하려는 경우 **이 응용 프로그램에 대한 액세스를 부여하기 전에 승인이 필요합니까?** 토글을 **예**로 설정합니다.

11. **선택 사항: 암호 Single Sign-On만을 사용하는 응용 프로그램의 경우** 해당 비즈니스 승인자가 승인된 사용자에 대한 이 응용 프로그램에 전송되는 암호를 지정하도록 허용하려는 경우 **승인자가 이 응용 프로그램에 대한 사용자의 암호를 설정하도록 허용하시겠습니까?** 토글을 **예**로 설정합니다.

12. **선택 사항:** 이 응용 프로그램에 대한 액세스를 승인할 수 있는 비즈니스 승인자를 지정하려면 레이블 **이 응용 프로그램에 대한 액세스는 누가 승인할 수 있습니까?** 옆의 선택기를 클릭하여 최대 10명의 개별 비즈니스 승인자를 선택합니다.

  >[!NOTE]
  >그룹은 지원되지 않습니다.
  >
  >

13. **선택 사항:** **역할을 표시하는 응용 프로그램의 경우** 셀프 서비스 승인된 사용자를 역할에 할당하려는 경우 **사용자를 이 응용 프로그램의 어떤 역할에 할당하시겠습니까?** 옆의 선택기를 클릭하여 이 사용자를 할당해야 하는 역할을 선택합니다.

14. 창 위쪽에서 **저장** 단추를 클릭하여 완료합니다.

셀프 서비스 응용 프로그램 구성을 완료한 후 사용자는 [응용 프로그램 액세스 패널](https://myapps.microsoft.com/)로 이동하고 **+ 추가** 단추를 클릭하여 셀프 서비스 액세스를 활성화한 앱을 찾을 수 있습니다. 비즈니스 승인자는 [응용 프로그램 액세스 패널](https://myapps.microsoft.com/)에서 알림을 볼 수도 있습니다. 사용자가 승인이 필요한 응용 프로그램에 대한 액세스를 요청한 경우 비즈니스 승인자에게 알리는 메일을 활성화할 수 있습니다. 

이러한 승인은 단일 승인 워크플로만 지원합니다. 즉, 여러 승인자를 지정하는 경우 모든 단일 승인자는 응용 프로그램에 대한 액세스를 승인합니다.

## <a name="next-steps"></a>다음 단계
[응용 프로그램 프록시를 사용하여 앱에 Single Sign-On 제공](active-directory-application-proxy-sso-using-kcd.md)
