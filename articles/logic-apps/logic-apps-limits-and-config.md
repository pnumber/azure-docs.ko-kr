---
title: "제한 및 구성 - Azure Logic Apps | Microsoft Docs"
description: "Azure Logic Apps에 대한 서비스 제한 및 구성 값"
services: logic-apps
documentationcenter: 
author: jeffhollan
manager: anneta
editor: 
ms.assetid: 75b52eeb-23a7-47dd-a42f-1351c6dfebdc
ms.service: logic-apps
ms.workload: integration
ms.tgt_pltfrm: na
ms.devlang: na
ms.topic: article
ms.date: 09/25/2017
ms.author: LADocs; jehollan
ms.openlocfilehash: 54a35607e107a09188373cc5f71bb3068b4c6bab
ms.sourcegitcommit: 0b02e180f02ca3acbfb2f91ca3e36989df0f2d9c
ms.translationtype: HT
ms.contentlocale: ko-KR
ms.lasthandoff: 03/05/2018
---
# <a name="logic-apps-limits-and-configuration"></a>Logic Apps 제한 및 구성

이 문서에서는 Azure Logic Apps에 대한 현재 제한 및 구성 세부 정보를 설명합니다.

## <a name="limits"></a>제한

### <a name="http-request-limits"></a>HTTP 요청 한도

다음은 단일 HTTP 요청 또는 커넥터 호출에 대한 제한 사항입니다.

#### <a name="timeout"></a>시간 제한

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 요청 시간 초과 | 120초 | 필요에 따라 [비동기 패턴](../logic-apps/logic-apps-create-api-app.md) 또는 [until 루프](logic-apps-control-flow-loops.md)를 보완할 수 있음 | 
|||| 

#### <a name="message-size"></a>메시지 크기

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 메시지 크기 | 100 MB | 일부 커넥터 및 API에서는 100MB를 지원하지 않을 수 있습니다. | 
| 식 평가 제한 | 131,072자 | `@concat()`, `@base64()`, `string`은 이 제한보다 길 수 없습니다. | 
|||| 

#### <a name="retry-policy"></a>다시 시도 정책

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 다시 시도 횟수 | 90 | 기본값은 4입니다. [재시도 정책 매개 변수](../logic-apps/logic-apps-workflow-actions-triggers.md)로 구성할 수 있습니다. | 
| 재시도 최대 지연 시간 | 1일 | [재시도 정책 매개 변수](../logic-apps/logic-apps-workflow-actions-triggers.md)로 구성할 수 있습니다. | 
| 재시도 최소 지연 시간 | 5초 | [재시도 정책 매개 변수](../logic-apps/logic-apps-workflow-actions-triggers.md)로 구성할 수 있습니다. |
|||| 

### <a name="run-duration-and-retention"></a>실행 기간 및 보존

다음은 단일 논리 앱 실행에 대한 제한 사항입니다.

| Name | 제한 | 
| ---- | ----- | 
| 실행 기간 | 90일 | 
| 저장소 보존 | 실행 시작 시간부터 90일 | 
| 최소 되풀이 간격 | 1초 </br>App Service 계획이 있는 논리 앱: 15초 | 
| 최대 되풀이 간격 | 500일 | 
||| 

정상적인 처리 흐름에서 실행 기간 또는 저장소 보존 한도를 초과하려면 [Logic Apps 팀에 문의](mailto://logicappsemail@microsoft.com)하여 요구 사항을 확인하세요.

### <a name="looping-and-debatching-limits"></a>반복 및 분리 한도

다음은 단일 논리 앱 실행에 대한 제한 사항입니다.

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| ForEach 항목 | 100,000 | [쿼리 작업](../connectors/connectors-native-query.md)을 사용하여 필요에 따라 큰 배열을 필터링할 수 있습니다. | 
| Until 반복 | 5,000 | | 
| SplitOn 항목 | 100,000 | | 
| ForEach 병렬 처리 | 50 | 기본값은 20입니다. <p>ForEach 루프에서 특정 수준의 병렬 처리를 설정하려면 `foreach` 작업에서 `runtimeConfiguration` 속성을 설정합니다. <p>ForEach 루프를 순차적으로 실행하려면 `foreach` 작업에서 `operationOptions` 속성을 “Sequential”로 설정합니다. | 
|||| 

### <a name="throughput-limits"></a>처리량 한도

다음은 단일 논리 앱 인스턴스에 대한 제한 사항입니다.

| Name | 제한 | 메모 | 
| ----- | ----- | ----- | 
| 5분당 작업 실행 | 100,000 | 한도를 300,000까지 높이려면 `High Througput` 모드에서 논리 앱을 실행합니다. 높은 처리량 모드를 구성하려면 워크플로 리소스의 `runtimeConfiguration` 아래에서 `operationOptions` 속성을 `OptimizedForHighThroughput`으로 설정합니다. <p>**참고**: 높은 처리량 모드는 미리 보기로 제공됩니다. 필요에 따라 여러 앱에 워크로드를 배포할 수도 있습니다. | 
| 작업 나가는 동시 호출 | ~2,500 | 필요에 따라 동시 요청 수를 줄이거나 기간을 단축합니다. | 
| 런타임 끝점: 들어오는 동시 호출 |~1,000 | 필요에 따라 동시 요청 수를 줄이거나 기간을 단축합니다. | 
| 런타임 끝점: 5분마다 호출을 읽습니다.  | 60,000 | 필요에 따라 여러 앱에 워크로드를 배포할 수 있습니다. | 
| 런타임 끝점: 5분마다 호출을 수행합니다.| 45,000 |필요에 따라 여러 앱에 워크로드를 배포할 수 있습니다. | 
|||| 

일반적인 처리에서 이러한 제한을 초과하거나 이러한 제한을 초과할 수 있는 부하 테스트를 실행하려면 [Logic Apps 팀에 문의](mailto://logicappsemail@microsoft.com)하여 요구 사항을 확인하세요.

### <a name="logic-app-definition-limits"></a>논리 앱 정의 제한

다음은 단일 논리 앱 정의에 대한 제한 사항입니다.

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 워크플로당 작업 | 500 | 이 제한을 확장하려면 필요에 따라 중첩된 워크플로를 추가할 수 있습니다. |
| 허용된 작업 중첩 깊이 | 8 | 이 제한을 확장하려면 필요에 따라 중첩된 워크플로를 추가할 수 있습니다. | 
| 구독당 지역별 워크플로 | 1000 | | 
| 워크플로당 트리거 | 10 | | 
| Switch 범위 사례 제한 | 25 | | 
| 워크플로당 변수의 수 | 250 | | 
| 식당 최대 문자 수 | 8,192 | | 
| 최대 `trackedProperties` 크기(자) | 16,000 | 
| `action`/`trigger` 이름 제한 | 80 | | 
| `description` 길이 제한 | 256 | | 
| `parameters` 제한 | 50 | | 
| `outputs` 제한 | 10 | | 
|||| 

<a name="custom-connector-limits"></a>

### <a name="custom-connector-limits"></a>사용자 지정 커넥터 제한

이러한 제한은 웹 API에서 만들 수 있는 사용자 지정 커넥터에 적용됩니다.

| Name | 제한 | 
| ---- | ----- | 
| 만들 수 있는 사용자 지정 커넥터의 수 | Azure 구독당 1,000개 | 
| 사용자 지정 커넥터에서 만든 각 연결에 대한 분당 요청 수 | 커넥터에서 만든 각 연결에 대해 500개 요청 |
||| 

### <a name="integration-account-limits"></a>통합 계정 제한

다음은 통합 계정에 추가할 수 있는 아티팩트에 대한 제한 사항입니다.

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 스키마 | 8MB | [Blob URI](../logic-apps/logic-apps-enterprise-integration-schemas.md)를 사용하여 2MB보다 큰 파일을 업로드할 수 있습니다. | 
| 맵(XSLT 파일) | 2MB | | 
| 런타임 끝점: 5분마다 호출을 읽습니다. | 60,000 | 필요에 따라 여러 계정에 워크로드를 배포할 수 있습니다. | 
| 런타임 끝점: 5분마다 호출을 수행합니다. | 45,000 | 필요에 따라 여러 계정에 워크로드를 배포할 수 있습니다. | 
| 런타임 끝점: 5분마다 호출 추적 | 45,000 | 필요에 따라 여러 계정에 워크로드를 배포할 수 있습니다. | 
| 런타임 끝점: 동시 호출 차단 | ~1,000 | 필요에 따라 동시 요청 수를 줄이거나 기간을 단축합니다. | 
|||| 

이러한 제한은 통합 계정에 추가할 수 있는 아티팩트의 수에 적용됩니다.

#### <a name="free-pricing-tier"></a>무료 가격 책정 계층

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 규약 | 10 | | 
| 기타 아티팩트 형식 | 25 | 아티팩트 형식에는 파트너, 스키마, 인증서 및 맵이 포함됩니다. 각 형식은 최대 수의 아티팩트를 포함할 수 있습니다. | 
|||| 

#### <a name="standard-pricing-tier"></a>표준 가격 책정 계층

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| 모든 아티팩트 형식 | 500 | 아티팩트 형식에는 계약, 파트너, 스키마, 인증서 및 맵이 포함됩니다. 각 형식은 최대 수의 아티팩트를 포함할 수 있습니다. | 
|||| 

### <a name="b2b-protocols-as2-x12-edifact-message-size"></a>B2B 프로토콜(AS2, X12, EDIFACT) 메시지 크기

다음은 B2B 프로토콜에 적용되는 제한 사항입니다.

| Name | 제한 | 메모 | 
| ---- | ----- | ----- | 
| AS2 | 50MB | 디코딩 및 인코딩에 적용됩니다. | 
| X12 | 50MB | 디코딩 및 인코딩에 적용됩니다. | 
| EDIFACT | 50MB | 디코딩 및 인코딩에 적용됩니다. | 
|||| 

<a name="configuration"></a>

## <a name="configuration-ip-addresses"></a>구성: IP 주소

### <a name="logic-apps-service"></a>Logic Apps 서비스

논리 앱이 [HTTP](../connectors/connectors-native-http.md) 또는 [HTTP + Swagger](../connectors/connectors-native-http-swagger.md) 또는 다른 HTTP 요청을 통해 직접 수행하는 호출은 이 목록의 IP 주소에서 온 것입니다.

|Logic Apps 지역|아웃바운드 IP|
|-----------------|-----------|
|오스트레일리아 동부|13.75.149.4, 104.210.91.55, 104.210.90.241|
|오스트레일리아 남동부|13.73.114.207, 13.77.3.139, 13.70.159.205|
|브라질 남부|191.235.82.221, 191.235.91.7, 191.234.182.26|
|캐나다 중부|52.233.29.92, 52.228.39.241, 52.228.39.244|
|캐나다 동부|52.232.128.155, 52.229.120.45, 52.229.126.25|
|인도 중부|52.172.154.168, 52.172.186.159, 52.172.185.79|
|미국 중부|13.67.236.125, 104.208.25.27, 40.122.170.198|
|동아시아|13.75.94.173, 40.83.127.19, 52.175.33.254|
|미국 동부|13.92.98.111, 40.121.91.41, 40.114.82.191|
|미국 동부 2|40.84.30.147, 104.208.155.200, 104.208.158.174|
|일본 동부|13.71.158.3, 13.73.4.207, 13.71.158.120|
|일본 서부|40.74.140.4, 104.214.137.243, 138.91.26.45|
|미국 중북부|168.62.248.37, 157.55.210.61, 157.55.212.238|
|북유럽|40.113.12.95, 52.178.165.215, 52.178.166.21|
|미국 중남부|104.210.144.48, 13.65.82.17, 13.66.52.232|
|동남아시아|13.76.133.155, 52.163.228.93, 52.163.230.166|
|인도 남부|52.172.50.24, 52.172.55.231, 52.172.52.0|
|미국 중서부|52.161.27.190, 52.161.18.218, 52.161.9.108|
|서유럽|40.68.222.65, 40.68.209.23, 13.95.147.65|
|인도 서부|104.211.164.80, 104.211.162.205, 104.211.164.136|
|미국 서부|52.160.92.112, 40.118.244.241, 40.118.241.243|
|미국 서부 2|13.66.210.167, 52.183.30.169, 52.183.29.132|
|영국 남부|51.140.74.14, 51.140.73.85, 51.140.78.44|
|영국 서부|51.141.54.185, 51.141.45.238, 51.141.47.136|
| | |

### <a name="connectors"></a>커넥터

[커넥터](../connectors/apis-list.md)가 수행하는 호출은 이 목록의 IP 주소에서 온 것입니다.

|Logic Apps 지역|아웃바운드 IP|
|-----------------|-----------|
|오스트레일리아 동부|40.126.251.213|
|오스트레일리아 남동부|40.127.80.34|
|브라질 남부|191.232.38.129|
|캐나다 중부|52.233.31.197, 52.228.42.205, 52.228.33.76, 52.228.34.13|
|캐나다 동부|52.229.123.98, 52.229.120.178, 52.229.126.202, 52.229.120.52|
|인도 중부|104.211.98.164|
|미국 중부|40.122.49.51|
|동아시아|23.99.116.181|
|미국 동부|191.237.41.52|
|미국 동부 2|104.208.233.100|
|일본 동부|40.115.186.96|
|일본 서부|40.74.130.77|
|미국 중북부|65.52.218.230|
|북유럽|104.45.93.9|
|미국 중남부|104.214.70.191|
|동남아시아|13.76.231.68|
|인도 남부|104.211.227.225|
|서유럽|40.115.50.13|
|인도 서부|104.211.161.203|
|미국 서부|104.40.51.248|
|영국 남부|51.140.80.51|
|영국 서부|51.141.47.105|
| | | 

## <a name="next-steps"></a>다음 단계  

* [첫 번째 논리 앱 만들기](../logic-apps/quickstart-create-first-logic-app-workflow.md)  
* [일반적인 예제 및 시나리오](../logic-apps/logic-apps-examples-and-scenarios.md)
* [비디오: Logic Apps으로 비즈니스 프로세스 자동화](http://channel9.msdn.com/Events/Build/2016/T694) 
* [비디오: Logic Apps와 시스템 통합](http://channel9.msdn.com/Events/Build/2016/P462)