---
title: 클라우드 인프라의 Adobe Commerce에 대한 휴일 서지 용량 요청
description: 성수기(약 11월 중순부터 1월 중순) 동안 Adobe은 클라우드 인프라에서 호스팅되는 모든 Adobe Commerce 가맹점에 트래픽 증가에 대비할 것을 권장합니다.
exl-id: 9d6910bf-30bc-4117-bf7f-a0316f9506b5
feature: Cloud, Paas
role: Admin
source-git-commit: 357e0acb1c849079ff0fe9f53fe386f60475c7f9
workflow-type: tm+mt
source-wordcount: '446'
ht-degree: 0%

---

# 클라우드 인프라의 Adobe Commerce에 대한 휴일 서지 용량 요청

성수기(약 11월 중순부터 1월 중순) 동안 Adobe은 클라우드 인프라에서 호스팅되는 모든 Adobe Commerce 가맹점에 트래픽 증가에 대비할 것을 권장합니다.

**트래픽 계획 및 예상**

클라우드 인프라의 모든 Adobe Commerce 판매자에게 권장합니다 [성수기 트래픽을 예측하는 방법에 대해 이 권장 사항 세트 활용](https://business.adobe.com/blog/how-to/the-5-ps-of-peak-season-performance-a-guide-to-preparing-your-infrastructure-for-high-traffic) 매년 가장 성수기인 휴일 영업 시즌에.

권장되는 예상 값을 완료한 후 추가 용량이 필요하다고 판단되는 날짜를 팀에서 확인한 경우 다음 단계로 이동하여 서지 용량을 요청하는 방법에 대한 정보를 확인하십시오.

**업사이징 내역 보기**

에게 정보를 요청하여 요청된 크기 조정 내역을 볼 수 있습니다. **CSM(Customer Success Manager)**.
각 크기 조정 요청에 대해 다음 정보를 사용할 수 있습니다.

* **시작 일자 크기 조정**: 업데이트 요청 날짜.
* **크기 종료일**: 클러스터가 이전 크기로 반환된 날짜입니다.
* **vCPU 크기**: 업사이즈 이후의 클러스터 크기입니다.
* **일 사용량**: 클러스터가 업사이징된 상태로 유지되는 기간(일)입니다.
* **기간 vCPU**: 사용된 일수만큼 vCPU 크기가 변경되었습니다. 예를 들어 vCPU 크기 192 x 25일은 4,800입니다.

**서지 용량 요청 중**

휴가철 동안 추가 용량의 필요성을 예상하는 클라우드 인프라의 Adobe Commerce 판매자는 [서지 용량 지원 티켓 제출](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-request-temporary-magento-upsize.html) 를 통해 [도움말 센터](/help/overview.md)티켓 내의 날짜 및 예상 용량 요구 사항을 나타냅니다. 용량을 늘리기 위해서는 라이선스가 부여된 초과 용량을 사용해야 합니다.

**이 티켓은 최소 48시간 영업시간 전에 미리 제출하는 것이 좋습니다. 또한 블랙 프라이데이/사이버 먼데이 기간 동안 용량이 제한되므로 가능한 한 미리 요청을 하도록 권장합니다.**


**추가 도움말?**

성수기 트래픽 준비에 대한 추가 지침이 필요하십니까? 클라우드 인프라의 Adobe Commerce 판매자는 성공적인 성수기를 준비하기 위한 도움말, 전략 및 계획 팁을 얻기 위해 Adobe 계정 팀에 문의할 수 있습니다. 또한 다음을 확인하는 것이 좋습니다. [Magento 블로그](https://magento.com/blog) 전략 팁은 연중 내내 확인할 수 있습니다.

## 수용작업량 검토에 관한 자료

지원 기술 자료에서:

* [클라우드에서 Adobe Commerce에 대한 CPU 할당 계산](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-cpu-allocation-calculation.html)
* [클라우드에서 Adobe Commerce에 대해 호스트 인스턴스의 업사이징이 필요한지 확인](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-if-upsize-for-hosts-instances-is-needed.html)
* [클라우드에서 Adobe Commerce에 대한 호스트의 CPU 구성 확인](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/magento-commerce-cloud-check-hosts-cpu-configuration.html)
* [클라우드에서 Adobe Commerce에 대한 가동 중단 확인 및 측정](https://experienceleague.adobe.com/docs/commerce-knowledge-base/kb/how-to/how-to-identify-outages.html)
