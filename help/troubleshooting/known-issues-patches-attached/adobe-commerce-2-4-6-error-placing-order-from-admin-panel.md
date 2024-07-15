---
title: Adobe Commerce 2.4.6 관리 패널에서 순서 지정 중 오류 발생
description: 이 문서에서는 Commerce 관리 패널에서 주문한 후 스토어 선택이 중단될 때 알려진 Adobe Commerce on cloud infrastructure 2.4.6 문제에 대한 패치를 제공합니다.
feature: Admin Workspace
role: Developer
exl-id: b30be5a5-3681-41db-9040-3624faed7c46
source-git-commit: 0ad52eceb776b71604c4f467a70c13191bb9a1eb
workflow-type: tm+mt
source-wordcount: '242'
ht-degree: 0%

---

# Adobe Commerce 2.4.6 관리 패널에서 순서 지정 중 오류 발생

이 문서에서는 Commerce 관리 패널에서 주문한 후 스토어 선택이 중단될 때 알려진 Adobe Commerce on cloud infrastructure 2.4.6 문제에 대한 패치를 제공합니다.

## 문제

관리자 패널에서 주문할 때 스토어 선택 사항이 남아 있습니다.

<u>재현 단계</u>

1. **[!UICONTROL Sales]** > **[!UICONTROL Orders]**(으)로 이동하여 주문을 만들 고객을 선택하십시오.
2. 스토어 선택기 화면에서 주문할 스토어를 선택합니다.

<u>예상 결과</u>

매장을 선택한 후 주문을 완료할 수 있습니다.

<u>실제 결과:</u>

스토어를 선택하면 스토어 선택기 페이지로 다시 리디렉션되며 주문을 만들 수 없습니다.

## 패치

다음 링크를 클릭하여 패치를 다운로드합니다.

[ACSD-52277_2.4.6.patch 다운로드](assets/ACSD-52277_2.4.6.patch.zip)

### 호환 가능한 Adobe Commerce 버전

이 패치는 Adobe Commerce on cloud infrastructure 및 Adobe Commerce on-premise 2.4.6 및 2.4.6-p1용으로 만들어졌으며 이와 호환됩니다.

## 패치 적용 방법

* 클라우드 인프라에서 Adobe Commerce용 패치를 적용하는 방법은 Commerce on Cloud Infrastructure Guide의 [Apply patches](/docs/commerce-cloud-service/user-guide/develop/upgrade/apply-patches.html)을(를) 참조하십시오.
* Adobe Commerce 온-프레미스에 대한 패치 적용 지침은 Commerce 업그레이드 가이드의 [패치 적용](/docs/commerce-operations/upgrade-guide/patches/apply.html?lang=en#composer)을 참조하십시오.
