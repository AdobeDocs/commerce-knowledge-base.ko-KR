---
title: Magento Order Management 제거 방법(MOM)
description: 이 문서에서는 MOM(Magento Order Management) 시스템을 제거하는 방법에 대해 설명합니다.
exl-id: 9b2adb30-a880-45a2-859e-be0da42bfd07
source-git-commit: 2aeb2355b74d1cdfc62b5e7c5aa04fcd0a654733
workflow-type: tm+mt
source-wordcount: '100'
ht-degree: 0%

---

# Magento Order Management 제거 방법(MOM)

1. [통합 사용 안 함 또는 사용](/docs/commerce-admin/systems/integrations/mcom.html#disable-or-enable-the-integration)의 단계에 따라 MOM 통합을 사용하지 않도록 설정하십시오.
1. [모듈 제거](/docs/commerce-operations/installation-guide/tutorials/uninstall-modules.html)의 단계에 따라 MOM 모듈을 사용하지 않도록 설정하십시오.
1. 전체 주문 데이터를 추출하기 위해 API를 제공합니다. Adobe에서 [저장소 순서 지정](https://commerce-docs.github.io/oms-documentation-archive/specifications/#magento.sales.order_repository)을 검토하여 자세히 알아볼 수 있습니다. | 주문 정보(order_repository)를 다루는 Magento OMS 문서. Adobe의 [사양 섹션](https://commerce-docs.github.io/oms-documentation-archive/specifications/#services)을(를) 사용합니다. | 다른 API를 사용하여 다양한 정보 유형을 추출하도록 OMS 문서 Magento
