---
title: "자습서: ArcGIS Online과 Azure Active Directory 통합 | Microsoft Docs"
description: "Azure Active Directory 및 ArcGIS Online 간에 Single Sign-On을 구성하는 방법에 대해 알아봅니다."
services: active-directory
documentationCenter: na
author: jeevansd
manager: femila
ms.reviewer: joflore
ms.assetid: a9e132a4-29e7-48bf-beb9-4148e617c8a9
ms.service: active-directory
ms.workload: identity
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 12/13/2017
ms.author: jeedes
ms.openlocfilehash: b09dd977cbf5c4273667167217e86bb79ac2a9d8
ms.sourcegitcommit: fa28ca091317eba4e55cef17766e72475bdd4c96
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 12/14/2017
---
# <a name="tutorial-azure-active-directory-integration-with-arcgis-online"></a>자습서: ArcGIS Online과 Azure Active Directory 통합

이 자습서에서는 Azure AD(Azure Active Directory)와 ArcGIS Online을 통합하는 방법에 대해 알아봅니다.

ArcGIS Online을 Azure AD와 통합하면 다음과 같은 이점이 제공됩니다.

- ArcGIS Online에 대한 액세스 권한이 있는 사용자를 Azure AD에서 제어할 수 있습니다.
- 사용자가 해당 Azure AD 계정으로 ArcGIS Online에 자동으로 로그온(Single Sign-on)되도록 설정할 수 있습니다.
- 단일 중앙 위치인 Azure Portal에서 계정을 관리할 수 있습니다.

Azure AD와 SaaS 앱 통합에 대한 자세한 내용은 [Azure Active Directory의 응용 프로그램 액세스 및 Single Sign-On이란 무엇인가요?](active-directory-appssoaccess-whatis.md)를 참조하세요.

## <a name="prerequisites"></a>필수 조건

ArcGIS Online과 Azure AD 통합을 구성하려면 다음 항목이 필요합니다.

- Azure AD 구독
- ArcGIS Online Single Sign-On이 설정된 구독

> [!NOTE]
> 이 자습서의 단계를 테스트하기 위해 프로덕션 환경을 사용하는 것은 바람직하지 않습니다.

이 자습서의 단계를 테스트하려면 다음 권장 사항을 준수해야 합니다.

- 꼭 필요한 경우가 아니면 프로덕션 환경을 사용하지 마세요.
- Azure AD 평가판 환경이 없으면 [1개월 평가판을 얻을](https://azure.microsoft.com/pricing/free-trial/) 수 있습니다.

## <a name="scenario-description"></a>시나리오 설명
이 자습서에서는 테스트 환경에서 Azure AD Single Sign-On을 테스트 합니다. 이 자습서에 설명된 시나리오는 다음 두 가지 주요 구성 요소로 이루어져 있습니다.

1. 갤러리에서 ArcGIS Online 추가
2. Azure AD Single Sign-on 구성 및 테스트

## <a name="adding-arcgis-online-from-the-gallery"></a>갤러리에서 ArcGIS Online 추가
ArcGIS Online의 Azure AD 통합을 구성하려면 갤러리의 ArcGIS Online을 관리되는 SaaS 앱 목록에 추가해야 합니다.

**갤러리에서 ArcGIS Online을 추가하려면 다음 단계를 수행합니다.**

1. **[Azure Portal](https://portal.azure.com)**의 왼쪽 탐색 창에서 **Azure Active Directory** 아이콘을 클릭합니다. 

    ![Azure Active Directory 단추][1]

2. **엔터프라이즈 응용 프로그램**으로 이동합니다. 그런 후 **모든 응용 프로그램**으로 이동합니다.

    ![엔터프라이즈 응용 프로그램 블레이드][2]
    
3. 새 응용 프로그램을 추가하려면 대화 상자 맨 위 있는 **새 응용 프로그램** 단추를 클릭합니다.

    ![새 응용 프로그램 단추][3]

4. 검색 상자에 **ArcGIS Online**을 입력하고 결과 패널에서 **ArcGIS Online**을 선택한 후 **추가** 단추를 클릭하여 응용 프로그램을 추가합니다.

    ![결과 목록의 ArcGIS Online](./media/active-directory-saas-arcgis-tutorial/tutorial_arcgisonline_addfromgallery.png)

## <a name="configure-and-test-azure-ad-single-sign-on"></a>Azure AD Single Sign-On 구성 및 테스트

이 섹션에서는 “Britta Simon”이라는 테스트 사용자를 기반으로 ArcGIS Online에서 Azure AD Single Sign-On을 구성하고 테스트합니다.

Single Sign-On이 작동하려면 Azure AD에서 Azure AD 사용자에 해당하는 ArcGIS Online 사용자가 누구인지 알고 있어야 합니다. 즉, Azure AD 사용자와 ArcGIS Online의 관련 사용자 간에 연결이 형성되어야 합니다.

ArcGIS Online에서 Azure AD의 **사용자 이름** 값을 **Username** 값으로 할당하여 링크 관계를 설정합니다.

ArcGIS Online에서 Azure AD Single Sign-On을 구성하고 테스트하려면 다음 구성 요소를 완료해야 합니다.

1. **[Azure AD Single Sign-On 구성](#configure-azure-ad-single-sign-on)** - 사용자가 이 기능을 사용할 수 있도록 합니다.
2. **[Azure AD 테스트 사용자 만들기](#create-an-azure-ad-test-user)** - Britta Simon으로 Azure AD Single Sign-On을 테스트하는 데 사용합니다.
3. **[ArcGIS Online 테스트 사용자 만들기](#create-a-arcgis-online-test-user)** - Britta Simon의 Azure AD 표현과 연결된 해당 사용자를 ArcGIS Online에 만듭니다.
4. **[Azure AD 테스트 사용자 할당](#assign-the-azure-ad-test-user)** - Britta Simon이 Azure AD Single Sign-on을 사용할 수 있도록 합니다.
5. **[Single Sign-On 테스트](#test-single-sign-on)** - 구성이 작동하는지 여부를 확인합니다.

### <a name="configure-azure-ad-single-sign-on"></a>Azure AD Single Sign-On 구성

이 섹션에서는 Azure Portal에서 Azure AD Single Sign-On을 사용하도록 설정하고 ArcGIS Online 응용 프로그램에서 Single Sign-On을 구성합니다.

**ArcGIS Online에서 Azure AD Single Sign-On을 구성하려면 다음 단계를 수행합니다.**

1. Azure Portal의 **ArcGIS Online** 응용 프로그램 통합 페이지에서 **Single Sign-On**을 클릭합니다.

    ![Single Sign-On 구성 링크][4]

2. **Single Sign-On** 대화 상자에서 **모드**를 **SAML 기반 로그온**으로 선택하여 Single Sign-On을 사용하도록 설정합니다.
 
    ![Single Sign-On 대화 상자](./media/active-directory-saas-arcgis-tutorial/tutorial_arcgisonline_samlbase.png)

3. **ArcGIS Online 도메인 및 URL** 섹션에서 다음 단계를 수행합니다.

    ![ArcGIS Online 도메인 및 URL Single Sign-On 정보](./media/active-directory-saas-arcgis-tutorial/tutorial_arcgisonline_url.png)

    a. **로그온 URL** 텍스트 상자에서 다음 패턴으로 URL을 입력합니다. `https://<companyname>.maps.arcgis.com`

    b. **식별자** 텍스트 상자에서 `<companyname>.maps.arcgis.com` 패턴을 사용하여 URL을 입력합니다.

    > [!NOTE] 
    > 이러한 값은 실제 값이 아닙니다. 실제 로그온 URL 및 식별자로 값을 업데이트합니다. 이 값을 가져오려면 [ArcGIS Online 클라이언트 지원 팀](http://support.esri.com/en/)에 문의하세요. 
 


4. **SAML 서명 인증서** 섹션에서 **메타데이터 XML**을 클릭한 후 컴퓨터에 메타데이터 파일을 저장합니다.

    ![인증서 다운로드 링크](./media/active-directory-saas-arcgis-tutorial/tutorial_arcgisonline_certificate.png) 

5. **저장** 단추를 클릭합니다.

    ![Single Sign-On 구성 저장 단추](./media/active-directory-saas-arcgis-tutorial/tutorial_general_400.png)

6. 다른 웹 브라우저 창에서 ArcGIS 회사 사이트에 관리자로 로그인합니다.

7. **설정 편집**을 클릭합니다.

    ![설정 편집](./media/active-directory-saas-arcgis-tutorial/ic784742.png "설정 편집")

8. **보안**을 클릭합니다.

    ![보안](./media/active-directory-saas-arcgis-tutorial/ic784743.png "보안")

9. **회사 로그인**에서 **ID 공급자 설정**을 클릭합니다.

    ![회사 로그인](./media/active-directory-saas-arcgis-tutorial/ic784744.png "회사 로그인")

10. **ID 공급자 설정** 구성 페이지에서 다음 단계를 수행합니다.
   
    ![ID 공급자 설정](./media/active-directory-saas-arcgis-tutorial/ic784745.png "ID 공급자 설정")
   
    a. **이름** 텍스트 상자에 조직의 이름을 입력합니다.

    b. **회사 ID 공급자에 대한 메타데이터를 다음을 사용하여 제공합니다**에서 **파일**을 선택합니다.

    c. 다운로드한 메타데이터 파일을 업로드하려면 **파일 선택**을 클릭합니다.

    d. **ID 공급자 설정**을 클릭합니다.

> [!TIP]
> 이제 앱을 설정하는 동안 [Azure Portal](https://portal.azure.com) 내에서 이러한 지침의 간결한 버전을 읽을 수 있습니다.  **Active Directory > 엔터프라이즈 응용 프로그램** 섹션에서 이 앱을 추가한 후에는 **Single Sign-On** 탭을 클릭하고 맨 아래에 있는 **구성** 섹션을 통해 포함된 설명서에 액세스하면 됩니다. 포함된 설명서 기능에 대한 자세한 내용은 [Azure AD 포함된 설명서]( https://go.microsoft.com/fwlink/?linkid=845985)에서 확인할 수 있습니다.
> 

### <a name="create-an-azure-ad-test-user"></a>Azure AD 테스트 사용자 만들기

이 섹션의 목적은 Azure Portal에서 Britta Simon이라는 테스트 사용자를 만드는 것입니다.

   ![Azure AD 테스트 사용자 만들기][100]

**Azure AD에서 테스트 사용자를 만들려면 다음 단계를 수행하세요.**

1. Azure Portal의 왼쪽 창에서 **Azure Active Directory** 단추를 클릭합니다.

    ![Azure Active Directory 단추](./media/active-directory-saas-arcgis-tutorial/create_aaduser_01.png)

2. 사용자 목록을 표시하려면 **사용자 및 그룹**으로 이동한 후 **모든 사용자**를 클릭합니다.

    !["사용자 및 그룹" 및 "모든 사용자" 링크](./media/active-directory-saas-arcgis-tutorial/create_aaduser_02.png)

3. **사용자** 대화 상자를 열려면 **모든 사용자** 대화 상자 위쪽에서 **추가**를 클릭합니다.

    ![추가 단추](./media/active-directory-saas-arcgis-tutorial/create_aaduser_03.png)

4. **사용자** 대화 상자에서 다음 단계를 수행합니다.

    ![사용자 대화 상자](./media/active-directory-saas-arcgis-tutorial/create_aaduser_04.png)

    a. **이름** 상자에 **BrittaSimon**을 입력합니다.

    b. **사용자 이름** 상자에 사용자인 Britta Simon의 전자 메일 주소를 입력합니다.

    c. **암호 표시** 확인란을 선택한 다음 **암호** 상자에 표시된 값을 적어둡니다.

    d. **만들기**를 클릭합니다.
 
### <a name="create-a-arcgis-online-test-user"></a>ArcGIS 온라인 테스트 사용자 만들기

Azure AD 사용자가 ArcGIS Online에 로그인할 수 있도록 하려면 ArcGIS Online으로 프로비전되어야 합니다.  
ArcGIS Online의 경우 프로비전은 수동 작업입니다.

**사용자 계정을 프로비전하려면 다음 단계를 수행합니다.**

1. **ArcGIS** 테넌트에 로그인합니다.

2. **멤버 초대**를 클릭합니다.
   
    ![멤버 초대](./media/active-directory-saas-arcgis-tutorial/ic784747.png "멤버 초대")

3. **전자 메일을 보내지 않고 멤버를 자동으로 추가**를 선택하고 **다음**을 클릭합니다.
   
    ![멤버를 자동으로 추가](./media/active-directory-saas-arcgis-tutorial/ic784748.png "멤버를 자동으로 추가")

4. **멤버** 대화 상자 페이지에서 다음 단계를 수행합니다.
   
     ![추가 및 검토](./media/active-directory-saas-arcgis-tutorial/ic784749.png "추가 및 검토")
    
     a. 프로비전하려는 유효한 AAD 계정의 **전자 메일**, **이름** 및 **성**을 입력합니다.
  
     b. **추가 및 검토**를 클릭합니다.
5. 입력한 데이터를 검토한 다음 **멤버 추가**를 클릭합니다.
   
    ![멤버 추가](./media/active-directory-saas-arcgis-tutorial/ic784750.png "멤버 추가")
        
    > [!NOTE]
    > Azure Active Directory 계정 보유자는 활성화되기 전에 전자 메일을 받고 링크를 따라 계정을 확인합니다.

### <a name="assign-the-azure-ad-test-user"></a>Azure AD 테스트 사용자 할당

이 섹션에서는 Azure Single Sign-On을 사용할 수 있도록 Britta Simon에게 ArcGIS Online에 대한 액세스 권한을 부여합니다.

![사용자 역할 할당][200] 

**Britta Simon을 ArcGIS Online에 할당하려면 다음 단계를 수행합니다.**

1. Azure Portal에서 응용 프로그램 보기를 연 다음 디렉터리 보기로 이동하고 **엔터프라이즈 응용 프로그램**으로 이동한 후 **모든 응용 프로그램**을 클릭합니다.

    ![사용자 할당][201] 

2. 응용 프로그램 목록에서 **ArcGIS Online**을 선택합니다.

    ![응용 프로그램 목록의 ArcGIS Online 링크](./media/active-directory-saas-arcgis-tutorial/tutorial_arcgisonline_app.png)  

3. 왼쪽 메뉴에서 **사용자 및 그룹**을 클릭합니다.

    !["사용자 및 그룹" 링크][202]

4. **추가** 단추를 클릭합니다. 그런 후 **할당 추가** 대화 상자에서 **사용자 및 그룹**을 선택합니다.

    ![할당 추가 창][203]

5. **사용자 및 그룹** 대화 상자의 사용자 목록에서 **Britta Simon**을 선택합니다.

6. **사용자 및 그룹** 대화 상자에서 **선택** 단추를 클릭합니다.

7. **할당 추가** 대화 상자에서 **할당** 단추를 클릭합니다.
    
### <a name="test-single-sign-on"></a>Single Sign-On 테스트

이 섹션에서는 액세스 패널을 사용하여 Azure AD Single Sign-On 구성을 테스트합니다.

액세스 패널에서 ArcGIS Online 타일을 클릭하면 ArcGIS Online 응용 프로그램에 자동으로 로그온됩니다.
액세스 패널에 대한 자세한 내용은 [액세스 패널 소개](active-directory-saas-access-panel-introduction.md)를 참조하세요. 

## <a name="additional-resources"></a>추가 리소스

* [Azure Active Directory와 SaaS Apps를 통합하는 방법에 대한 자습서 목록](active-directory-saas-tutorial-list.md)
* [Azure Active Directory로 응용 프로그램 액세스 및 Single Sign-On이란 무엇입니까?](active-directory-appssoaccess-whatis.md)

<!--Image references-->

[1]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_01.png
[2]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_02.png
[3]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_03.png
[4]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_04.png

[100]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_100.png

[200]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_200.png
[201]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_201.png
[202]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_202.png
[203]: ./media/active-directory-saas-arcgis-tutorial/tutorial_general_203.png

