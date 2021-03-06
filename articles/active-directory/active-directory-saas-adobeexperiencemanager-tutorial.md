---
title: "자습서: Adobe Experience Manager와 Azure Active Directory 통합 | Microsoft Docs"
description: "Azure Active Directory 및 Adobe Experience Manager 간에 Single Sign-On을 구성하는 방법에 대해 알아봅니다."
services: active-directory
documentationCenter: na
author: jeevansd
manager: mtillman
ms.reviewer: joflore
ms.assetid: 88a95bb5-c17c-474f-bb92-1f80f5344b5a
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 11/28/2017
ms.author: jeedes
ms.openlocfilehash: c366e314b77cd3344a90826b22b96a45e35b0b4e
ms.sourcegitcommit: b32d6948033e7f85e3362e13347a664c0aaa04c1
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 02/13/2018
---
# <a name="tutorial-azure-active-directory-integration-with-adobe-experience-manager"></a>자습서: Adobe Experience Manager와 Azure Active Directory 통합

이 자습서에서는 Azure AD(Azure Active Directory)와 Adobe Experience Manager를 통합하는 방법을 알아봅니다.

Adobe Experience Manager를 Azure AD와 통합하면 다음과 같은 혜택이 있습니다.

- Azure AD에서 Adobe Experience Manager에 액세스할 수 있는 사용자를 제어할 수 있습니다.
- 사용자가 자신의 Azure AD 계정으로 Adobe Experience Manager에 자동으로 로그인되도록 설정할 수 있습니다.
- 단일 중앙 위치인 Azure Portal에서 계정을 관리할 수 있습니다.

Azure AD와 SaaS 앱 통합에 대한 자세한 내용은 [Azure Active Directory를 사용한 응용 프로그램 액세스 및 Single Sign-On이란 무엇인가요?](active-directory-appssoaccess-whatis.md)를 참조하세요.

## <a name="prerequisites"></a>필수 조건

Adobe Experience Manager와 Azure AD 통합을 구성하려면 다음 항목이 필요합니다.

- Azure AD 구독
- Adobe Experience Manager Single Sign-On이 설정된 구독

> [!NOTE]
> 이 자습서의 단계를 테스트하기 위해 프로덕션 환경을 사용하는 것은 바람직하지 않습니다.

이 자습서의 단계를 테스트하려면 다음 권장 사항을 따릅니다.

- 꼭 필요한 경우가 아니면 프로덕션 환경을 사용하지 마세요.
- Azure AD 평가판 환경이 없으면 [1개월 평가판](https://azure.microsoft.com/pricing/free-trial/)을 받습니다.

## <a name="scenario-description"></a>시나리오 설명
이 자습서에서는 테스트 환경에서 Azure AD Single Sign-On을 테스트 합니다. 이 자습서에 설명된 시나리오는 다음 두 가지 주요 구성 요소로 이루어져 있습니다.

1. 갤러리에서 Adobe Experience Manager 추가
2. Azure AD Single Sign-on 구성 및 테스트

## <a name="add-adobe-experience-manager-from-the-gallery"></a>갤러리에서 Adobe Experience Manager 추가
Adobe Experience Manager의 Azure AD 통합을 구성하려면 갤러리의 Adobe Experience Manager를 관리되는 SaaS 앱 목록에 추가해야 합니다.

**갤러리에서 Adobe Experience Manager를 추가하려면 다음 단계를 수행합니다.**

1. [Azure Portal](https://portal.azure.com)의 왼쪽 창에서 **Azure Active Directory** 아이콘을 선택합니다. 

    ![Azure Active Directory 단추][1]

2. **엔터프라이즈 응용 프로그램**으로 이동합니다. 그런 후 **모든 응용 프로그램**으로 이동합니다.

    ![엔터프라이즈 응용 프로그램 블레이드][2]
    
3. 새 응용 프로그램을 추가하려면 대화 상자 맨 위 있는 **새 응용 프로그램** 단추를 선택합니다.

    ![새 응용 프로그램 단추][3]

4. 검색 상자에 **Adobe Experience Manager**를 입력합니다. 결과 패널에서 **Adobe Experience Manager**를 선택한 다음, **추가**를 선택하여 응용 프로그램을 추가합니다.

    ![결과 목록의 Adobe Experience Manager](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD Single Sign-On 구성 및 테스트

이 섹션에서는 "Britta Simon"이라는 테스트 사용자를 기반으로 Adobe Experience Manager에서 Azure AD Single Sign-On을 구성하고 테스트합니다.

Single Sign-On이 작동하려면 Azure AD에서 Azure AD 사용자에 해당하는 Adobe Experience Manager 사용자가 누구인지 알고 있어야 합니다. 즉, Azure AD 사용자와 Adobe Experience Manager의 관련 사용자 간에 연결이 형성되어야 합니다.

Adobe Experience Manager에서 Azure AD의 **사용자 이름**과 동일한 **Username** 값을 제공합니다. 이렇게 해서 두 사용자 간의 연결 관계를 형성했습니다. 

Adobe Experience Manager에서 Azure AD Single Sign-On을 구성하고 테스트하려면 다음 구성 요소를 완료합니다.

1. [Azure AD Single Sign-On 구성](#configure-azure-ad-single-sign-on) - 사용자가 이 기능을 사용할 수 있도록 합니다.
2. [Azure AD 테스트 사용자 만들기](#create-an-azure-ad-test-user) - Britta Simon으로 Azure AD Single Sign-On을 테스트하는 데 사용합니다.
3. [Adobe Experience Manager 테스트 사용자 만들기](#create-an-adobe-experience-manager-test-user) - Britta Simon의 Azure AD 표현과 연결된 해당 사용자를 Adobe Experience Manager에 만듭니다.
4. [Azure AD 테스트 사용자 할당](#assign-the-azure-ad-test-user) - Britta Simon이 Azure AD Single Sign-on을 사용할 수 있도록 합니다.
5. [Single Sign-on 테스트](#test-single-sign-on) - 구성이 작동하는지 여부를 확인합니다.

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD Single Sign-On 구성

이 섹션에서는 Azure Portal에서 Azure AD Single Sign-On을 사용하도록 설정하고 Adobe Experience Manager 응용 프로그램에서 Single Sign-On을 구성합니다.

**Adobe Experience Manager에서 Azure AD Single Sign-On을 구성하려면 다음 단계를 수행합니다.**

1. Azure Portal의 **Adobe Experience Manager** 응용 프로그램 통합 페이지에서 **Single Sign-On**을 선택합니다.

    ![Single Sign-On 구성 링크][4]

2. Single Sign-On을 사용하려면 **Single Sign-On** 대화 상자의 **모드** 드롭다운 메뉴에서 **SAML 기반 로그온**을 선택합니다.
 
    ![Single Sign-On 대화 상자](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_samlbase.png)

3. **Adobe Experience Manager 도메인 및 URL** 섹션에서 **IdP** 모드로 앱을 구성하려는 경우 다음 단계를 수행합니다.

    ![Adobe Experience Manager 도메인 및 URL Single Sign-On 정보](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_url1.png)

    a. **식별자** 상자에 AEM 서버에 대해서도 정의한 고유한 값을 입력합니다. 

    나. **회신 URL** 상자에 `https://<AEM Server Url>/saml_login` 패턴으로 URL을 입력합니다.

    > [!NOTE] 
    > 이러한 값은 실제 값이 아닙니다. 실제 식별자 및 회신 URL로 해당 값을 업데이트합니다. 이러한 값을 얻으려면 [Adobe Experience Manager 지원팀](https://helpx.adobe.com/support/experience-manager.html)에 문의하세요.
 
4. **고급 URL 설정 표시**를 선택합니다. **SP** 시작 모드로 응용 프로그램을 구성하려는 경우 다음 단계를 수행합니다.

    ![Adobe Experience Manager 도메인 및 URL Single Sign-On 정보](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_spconfigure.png)

    **로그온 URL** 상자에 Adobe Experience Manager 서버 URL을 입력합니다. 

5. **SAML 서명 인증서** 섹션에서 **인증서(Base64)**를 선택합니다. 그런 다음, 컴퓨터에 인증서 파일을 저장합니다.

    ![인증서 다운로드 링크](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_certificate.png) 

6. Adobe Experience Manager 구성 섹션에서 구성 로그온 창을 열려면 **Adobe Experience Manager** 구성을 선택합니다. 빠른 참조 섹션에서 **SAML 로그온 서비스 URL**, **SAML 엔터티 ID** 및 **로그아웃 ID**를 복사합니다.

    ![구성 섹션 링크](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_configure.png) 

7. **저장**을 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_400.png)

8. 다른 브라우저 창에서 **Adobe Experience Manager** 관리자 포털을 엽니다.

9. **설정** > **보안** > **사용자**를 선택합니다.

    ![Single Sign-On 저장 단추 구성](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_user.png)

10. **관리자** 또는 다른 관련 사용자를 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin6.png)

11. **계정 설정** > **TrustStore 관리**를 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_managetrust.png)

12. **CER 파일의 인증서 추가**에서 **인증서 파일 선택**을 클릭합니다. Azure Portal에서 다운로드한 인증서 파일을 찾아서 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_user2.png)

13. 인증서는 TrustStore에 추가됩니다. 인증서의 별칭을 적어둡니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin7.png)

14. **사용자** 페이지에서 **인증 서비스**를 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin8.png)

15. **계정 설정** > **키 저장소 만들기/관리**를 선택합니다. 암호를 제공하여 키 저장소를 만듭니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin9.png)

16. 관리 화면으로 돌아갑니다. **설정** > **작업** > **웹 콘솔**을 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin1.png)

    구성 페이지가 열립니다.

    ![Single Sign-On 저장 단추 구성](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin2.png)

17. **Adobe Granite SAML 2.0 인증 처리기**를 찾습니다. **추가** 아이콘을 선택합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin3.png)

19. 이 페이지에서 다음 작업을 수행합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_admin4.png)

    a. **경로** 상자에 **/**를 입력합니다.

    나. **IDP URL** 상자에 Azure Portal에서 복사한 **SAML 로그온 서비스 URL** 값을 입력합니다.

    다. **IDP 인증서 별칭** 상자에 TrustStore에서 추가한 **인증서 별칭** 값을 입력합니다.

    d. Azure Portal에서 구성한 고유의 **SAML 엔터티 ID** 값을 **보안 제공 엔터티 ID** 상자에 입력합니다.

    e. Azure Portal에서 구성한 **회신 URL** 값을 **어설션 소비자 서비스 URL** 상자에 입력합니다.

    f. 키 저장소에서 설정한 **암호**를 **키 저장소 암호** 상자에 입력합니다.

    g. 자신의 사례와 관련된 **이름 ID** 또는 다른 사용자 ID를 **사용자 특성 ID** 상자에 입력합니다.

    h. **CRX 사용자 자동 작성**을 선택합니다.

    i. **로그아웃 URL** 상자에 Azure Portal에서 얻은 **로그아웃 URL** 값을 입력합니다.

    j. **저장**을 선택합니다.

> [!TIP]
> 이제 앱을 설정하는 동안 [Azure Portal](https://portal.azure.com) 내에서 이러한 지침의 간결한 버전을 읽을 수 있습니다. **Active Directory** > **엔터프라이즈 응용 프로그램** 섹션에서 이 앱을 추가한 후 **Single Sign-On** 탭을 선택합니다. 그런 다음 맨 아래에 있는 **구성** 섹션을 통해 포함된 설명서에 액세스합니다. 포함된 설명서 기능에 대한 자세한 내용은 [Azure AD 포함된 설명서]( https://go.microsoft.com/fwlink/?linkid=845985)에서 확인할 수 있습니다.

### <a name="create-an-azure-ad-test-user"></a>Azure AD 테스트 사용자 만들기

이 섹션의 목적은 Azure Portal에서 Britta Simon이라는 테스트 사용자를 만드는 것입니다.

   ![Azure AD 테스트 사용자 만들기][100]

**Azure AD에서 테스트 사용자를 만들려면 다음 단계를 수행하세요.**

1. Azure Portal의 왼쪽 창에서 **Azure Active Directory** 단추를 선택합니다.

    ![Azure Active Directory 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/create_aaduser_01.png)

2. 사용자 목록을 표시하려면 **사용자 및 그룹**으로 이동한 후 **모든 사용자**를 선택합니다.

    !["사용자 및 그룹" 및 "모든 사용자" 링크](./media/active-directory-saas-adobeexperiencemanager-tutorial/create_aaduser_02.png)

3. **사용자** 대화 상자를 열려면 **모든 사용자** 대화 상자 위쪽에서 **추가**를 선택합니다.

    ![추가 단추](./media/active-directory-saas-adobeexperiencemanager-tutorial/create_aaduser_03.png)

4. **사용자** 대화 상자에서 다음 단계를 수행합니다.

    ![사용자 대화 상자](./media/active-directory-saas-adobeexperiencemanager-tutorial/create_aaduser_04.png)

    a. **이름** 상자에 **BrittaSimon**을 입력합니다.

    나. **사용자 이름** 상자에 사용자인 Britta Simon의 전자 메일 주소를 입력합니다.

    다. **암호 표시** 확인란을 선택합니다. **암호** 상자에 표시된 값을 적어둡니다.

    d. **만들기**를 선택합니다.
  
### <a name="create-an-adobe-experience-manager-test-user"></a>Adobe Experience Manager 테스트 사용자 만들기

이 섹션에서는 Adobe Experience Manager에서 Britta Simon이라는 사용자를 만듭니다. **CRX 사용자 자동 작성** 옵션을 선택한 경우 사용자는 인증을 성공한 후에 자동으로 생성됩니다. 

수동으로 사용자를 만들려는 경우 [Adobe Experience Manager 지원팀](https://helpx.adobe.com/support/experience-manager.html)과 협력하여 Adobe Experience Manager 플랫폼에 사용자를 추가하세요. 

### <a name="assign-the-azure-ad-test-user"></a>Azure AD 테스트 사용자 할당

이 섹션에서는 Azure Single Sign-On을 사용할 수 있도록 Britta Simon에게 Adobe Experience Manager에 대한 액세스 권한을 부여합니다.

![사용자 역할 할당][200] 

**Britta Simon을 Adobe Experience Manager에 할당하려면 다음 단계를 수행합니다.**

1. Azure Portal에서 응용 프로그램 보기를 엽니다. 다음으로, 디렉터리 보기로 이동하여 **엔터프라이즈 응용 프로그램**을 선택한 다음, **모든 응용 프로그램**을 선택합니다.

    ![사용자 할당][201] 

2. 응용 프로그램 목록에서 **Adobe Experience Manager**를 선택합니다.

    ![응용 프로그램 목록의 Adobe Experience Manager 링크](./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_adobeexperiencemanager_app.png)  

3. 왼쪽 메뉴에서 **사용자 및 그룹**을 선택합니다.

    !["사용자 및 그룹" 링크][202]

4. **추가** 단추를 선택합니다. 그런 후 **할당 추가** 대화 상자에서 **사용자 및 그룹**을 선택합니다.

    ![할당 추가 창][203]

5. **사용자 및 그룹** 대화 상자의 사용자 목록에서 **Britta Simon**을 선택합니다.

6. **사용자 및 그룹** 대화 상자에서 **선택** 단추를 클릭합니다.

7. **할당 추가** 대화 상자에서 **할당** 단추를 선택합니다.
    
### <a name="test-single-sign-on"></a>Single Sign-On 테스트

이 섹션에서는 액세스 패널을 사용하여 Azure AD Single Sign-On 구성을 테스트합니다.

액세스 패널에서 Adobe Experience Manager 타일을 선택하면 Adobe Experience Manager 응용 프로그램에 자동으로 로그온됩니다.

액세스 패널에 대한 자세한 내용은 [액세스 패널 소개](active-directory-saas-access-panel-introduction.md)를 참조하세요. 

## <a name="additional-resources"></a>추가 리소스

* [Azure Active Directory를 사용하여 SaaS 앱을 통합하는 방법에 대한 자습서 목록](active-directory-saas-tutorial-list.md)
* [Azure Active Directory로 응용 프로그램 액세스 및 Single Sign-On을 구현하는 방법](active-directory-appssoaccess-whatis.md)



<!--Image references-->

[1]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-adobeexperiencemanager-tutorial/tutorial_general_203.png

